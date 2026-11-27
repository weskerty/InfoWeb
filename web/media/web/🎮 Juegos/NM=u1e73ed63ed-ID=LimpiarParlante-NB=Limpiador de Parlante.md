<h1>Limpiador de Parlante</h1>
<button id="parlante-iniciar" type="button" aria-pressed="false" aria-describedby="parlante-nota">Iniciar</button>
<p id="parlante-estado" role="status" aria-live="polite" aria-atomic="true">Un patrón cada 20 segundos. Repite hasta detener.</p>
<p id="parlante-nota">Desconecta auricular si queres limpiar el parlante del telefono, pone el parlante hacia abajo y subi el volumen al maximo.</p>

<style>
  #parlante-iniciar { min-width: 160px; min-height: 48px; font-size: 1rem; }
  #parlante-estado { margin: 16px 0 12px; font-variant-numeric: tabular-nums; }
  #parlante-nota { max-width: 52ch; color: var(--RD_MF, inherit); font-size: .9rem; line-height: 1.6; }
</style>

<script>
(() => {
  'use strict';

  const button = document.getElementById('parlante-iniciar');
  const status = document.getElementById('parlante-estado');
  const content = document.getElementById('content') || document;
  const AudioContextClass = window.AudioContext || window.webkitAudioContext;
  const listeners = new AbortController();
  const closing = new Set();
  const DURATION = 20;
  const FADE = 0.05;

  const PATTERNS = [
    { label: 'Pulsos graves · 165 Hz', low: 165, high: 165, pulse: 9, level: 0.75 },
    { label: 'Barrido grave lento · 100–400 Hz', low: 100, high: 400, leg: 5, level: 0.70 },
    { label: 'Barrido grave rápido · 100–400 Hz', low: 100, high: 400, leg: 0.5, level: 0.65 },
    { label: 'Barrido grave pulsado · 100–400 Hz', low: 100, high: 400, leg: 2.5, pulse: 4, level: 0.70 },
    { label: 'Barrido agudo experimental · 3.000–9.000 Hz', low: 3000, high: 9000, leg: 1 / 6, level: 0.16 },
    { label: 'Barrido amplio exploratorio · 80–12.000 Hz', low: 80, high: 12000, leg: 2, level: 0.20 }
  ];

  let active = null;
  let destroyed = false;

  function setButton(running) {
    button.textContent = running ? 'Detener' : 'Iniciar';
    button.setAttribute('aria-pressed', String(running));
  }

  function releaseVoice(session) {
    const voice = session.voice;
    if (!voice) return;
    session.voice = null;
    voice.osc.onended = null;
    try { voice.osc.stop(); } catch (_) {}
    voice.osc.disconnect();
    voice.gain.disconnect();
  }

  function dispose(session) {
    if (!session || session.disposed) return;
    session.disposed = true;
    session.running = false;
    clearTimeout(session.closeTimer);
    closing.delete(session);
    const ctx = session.ctx;
    if (ctx) ctx.onstatechange = null;
    releaseVoice(session);
    if (session.master) session.master.disconnect();
    session.master = null;
    session.ctx = null;
    if (ctx && ctx.state !== 'closed') {
      try { ctx.close().catch(() => {}); } catch (_) {}
    }
  }

  function stop(message = 'Detenido. Podés iniciar otra vez.', immediate = false) {
    const session = active;
    active = null;
    if (!destroyed) {
      setButton(false);
      status.textContent = message;
    }

    if (session) {
      session.running = false;
      const ctx = session.ctx;
      if (!immediate && session.voice && ctx && ctx.state === 'running') {
        closing.add(session);
        ctx.onstatechange = null;
        session.voice.osc.onended = null;
        try {
          const now = ctx.currentTime;
          session.master.gain.cancelScheduledValues(now);
          session.master.gain.setValueAtTime(1, now);
          session.master.gain.linearRampToValueAtTime(0, now + FADE);
          session.voice.osc.stop(now + FADE);
          session.closeTimer = setTimeout(() => dispose(session), 80);
        } catch (_) {
          dispose(session);
        }
      } else {
        dispose(session);
      }
    }

    if (immediate) {
      for (const pending of closing) dispose(pending);
    }
  }

  function playStage(session, index) {
    if (destroyed || active !== session || !session.running) return;
    const pattern = PATTERNS[index];
    const ctx = session.ctx;
    const osc = ctx.createOscillator();
    const gain = ctx.createGain();
    const start = ctx.currentTime;
    const end = start + DURATION;
    session.voice = { osc, gain };

    osc.type = 'sine';
    osc.connect(gain);
    gain.connect(session.master);
    osc.frequency.setValueAtTime(pattern.low, start);

    if (pattern.leg) {
      let upward = true;
      for (let t = start; t < end - 0.000001; t += pattern.leg) {
        osc.frequency.exponentialRampToValueAtTime(
          upward ? pattern.high : pattern.low,
          Math.min(t + pattern.leg, end)
        );
        upward = !upward;
      }
    }

    gain.gain.setValueAtTime(0, start);
    gain.gain.linearRampToValueAtTime(pattern.level, start + FADE);
    if (pattern.pulse) {
      const period = 1 / pattern.pulse;
      for (let t = start + FADE; t + period <= end - FADE; t += period) {
        gain.gain.linearRampToValueAtTime(pattern.level * 0.15, t + period / 2);
        gain.gain.linearRampToValueAtTime(pattern.level, t + period);
      }
    }
    gain.gain.setValueAtTime(pattern.level, end - FADE);
    gain.gain.linearRampToValueAtTime(0, end);

    osc.onended = () => {
      if (destroyed || active !== session || !session.running) return;
      releaseVoice(session);
      const next = (index + 1) % PATTERNS.length;
      if (next === 0) session.round += 1;
      try {
        playStage(session, next);
      } catch (_) {
        stop('El audio se interrumpió. Pulsá Iniciar para volver a intentar.', true);
      }
    };

    status.textContent = pattern.label + ' · 20 s · Vuelta ' + session.round;
    osc.start(start);
    osc.stop(end);
  }

  async function start() {
    if (destroyed || active || document.hidden) return;
    const session = { ctx: null, master: null, voice: null, running: false, disposed: false, closeTimer: null, round: 1 };
    active = session;
    setButton(true);
    status.textContent = 'Iniciando…';

    try {
      const ctx = session.ctx = new AudioContextClass();
      session.master = ctx.createGain();
      session.master.gain.value = 1;
      session.master.connect(ctx.destination);
      ctx.onstatechange = () => {
        if (active === session && session.running && ctx.state !== 'running') {
          stop('El audio se interrumpió. Pulsá Iniciar para continuar.', true);
        }
      };
      await ctx.resume();

      if (destroyed || active !== session || document.hidden) {
        if (active === session) stop('Detenido al ocultar la página.', true);
        else dispose(session);
        return;
      }
      if (ctx.state !== 'running') throw new Error('Audio no disponible');
      session.running = true;
      playStage(session, 0);
    } catch (_) {
      if (active === session) stop('No se pudo iniciar el audio. Pulsá Iniciar para volver a intentar.', true);
      else dispose(session);
    }
  }

  function destroy() {
    if (destroyed) return;
    destroyed = true;
    stop('', true);
    listeners.abort();
  }

  const options = { signal: listeners.signal };
  button.addEventListener('click', () => {
    if (active) stop();
    else start();
  }, options);
  content.addEventListener('contentUnload', event => {
    if (event.target === content) destroy();
  }, options);
  document.addEventListener('visibilitychange', () => {
    if (document.hidden) stop('Detenido al ocultar la página. Pulsá Iniciar para continuar.', true);
  }, options);
  window.addEventListener('pagehide', () => {
    stop('Detenido al salir de la página. Pulsá Iniciar para continuar.', true);
  }, options);

  if (!AudioContextClass) {
    button.disabled = true;
    status.textContent = 'Este navegador no admite la generación de audio.';
  }
})();
</script>
