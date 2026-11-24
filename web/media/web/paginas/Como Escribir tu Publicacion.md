## ✍️ Como escribir tu publicacion

En el cuadro de descripcion se escribe texto simple con algunos simbolos. En cada ejemplo esta **lo que se escribe** y abajo **como queda**.

Imagenes y videos: solo enlaces externos (que empiecen con https://).

---

## 🔤 Texto

Enter pasa a la linea siguiente. Una linea en blanco empieza un parrafo nuevo.

Se escribe:
```
**negrita**, *cursiva* y ~~tachado~~
Esta linea sigue justo abajo.

Despues de una linea en blanco: parrafo nuevo.
```

Queda:

**negrita**, *cursiva* y ~~tachado~~
Esta linea sigue justo abajo.

Despues de una linea en blanco: parrafo nuevo.

---

## 🖍️ Resaltar

Entre **==** y **==**. Junto con el tachado sirve para ofertas.

Se escribe:
```
Precio normal ~~50.000 Gs~~, hoy ==35.000 Gs==
```

Queda:

Precio normal ~~50.000 Gs~~, hoy ==35.000 Gs==

---

## 🔠 Titulos

Una linea que empieza con **#** y un espacio. Mas **#**, mas chico.

Se escribe:
```
# Titulo grande
## Titulo mediano
### Titulo chico
```

Queda:

# Titulo grande
## Titulo mediano
### Titulo chico

---

## 📝 Listas

Con guion para puntos, con numero y punto para pasos.

Se escribe:
```
- un item
- otro item

1. Elegi el color
2. Agregalo al carrito
3. Pedi por WhatsApp
```

Queda:

- un item
- otro item

1. Elegi el color
2. Agregalo al carrito
3. Pedi por WhatsApp

Con casillas:

Se escribe:
```
- [x] Pagado
- [x] Empaquetado
- [ ] Enviado
```

Queda:

- [x] Pagado
- [x] Empaquetado
- [ ] Enviado

---

## 🔗 Enlaces

Texto entre **[ ]** y la direccion entre **( )**. Una direccion sola tambien queda como enlace.

Se escribe:
```
[Ver la tienda](https://cheagana.com)

https://cheagana.com
```

Queda:

[Ver la tienda](https://cheagana.com)

https://cheagana.com

---

## ➖ Linea separadora

Tres guiones solos, con una linea en blanco arriba y abajo. Sin la linea en blanco de arriba, el texto de encima se vuelve titulo.

Se escribe:
```
Arriba

---

Abajo
```

Queda:

Arriba

---

Abajo

---

## 📷 Fotos

**!** y la descripcion entre **[ ]**, el enlace de la foto entre **( )**. La descripcion la leen los buscadores y los lectores de pantalla.

Se escribe:
```
![Adaptador USB-C](https://link-de-la-foto.jpg)
```

Queda:

![Adaptador USB-C](web/adjuntos/USBOTGSA/90757.avif)

Tamano: despues de la descripcion, un espacio y **=ANCHOx** (la x va siempre). Ancho en pixeles o en %. Sin tamano, la foto ocupa lo que mide.

Se escribe:
```
![Adaptador =150x](https://link-de-la-foto.jpg)

![Adaptador =50%x](https://link-de-la-foto.jpg)
```

Queda:

![Adaptador =150x](web/adjuntos/USBOTGSA/90757.avif)

![Adaptador =50%x](web/adjuntos/USBOTGSA/90757.avif)

---

## 🖼️ Galeria automatica

3 o mas fotos pegadas, o una debajo de otra sin linea en blanco, se convierten solas en una galeria que se desliza.

Se escribe:
```
![Foto 1](https://link-1.jpg)
![Foto 2](https://link-2.jpg)
![Foto 3](https://link-3.jpg)
```

Queda:

![Ejemplo](web/adjuntos/USBOTGSA/90757.avif)
![Conectando hub, teclado y raton](web/adjuntos/USBOTGSA/104954.avif)
![Ejemplo de uso](web/adjuntos/USBOTGSA/104964.avif)

Si alguna foto lleva tamano o enlace no se arma la galeria. Para dejarlas sueltas, una linea en blanco entre foto y foto.

---

## 🧱 Foto al lado del texto

Dos columnas iguales. En celular siguen una al lado de la otra.

Se escribe:
```
@grids grid-cols-2 gap-4 items-center
@grid
![Adaptador](https://link-de-la-foto.jpg)
@grid
**Adaptador USB-C**
Conecta un pendrive o mouse al celular.
@end
```

Queda:

@grids grid-cols-2 gap-4 items-center
@grid
![Adaptador](web/adjuntos/USBOTGSA/90757.avif)
@grid
**Adaptador USB-C**
Conecta un pendrive o mouse al celular.
@end

Foto chica fija y el texto ocupa el resto:

Se escribe:
```
@flexs gap-4 items-center
@flex shrink-0
![Adaptador =120x](https://link-de-la-foto.jpg)
@flex flex-1
**Adaptador USB-C**
Texto al lado de una foto chica.
@end
```

Queda:

@flexs gap-4 items-center
@flex shrink-0
![Adaptador =120x](web/adjuntos/USBOTGSA/104964.avif)
@flex flex-1
**Adaptador USB-C**
Texto al lado de una foto chica.
@end

Fila de fotos (grid-cols-3 = 3 por fila):

Se escribe:
```
@grids grid-cols-3 gap-2
@grid
![Foto 1](https://link-1.jpg)
@grid
![Foto 2](https://link-2.jpg)
@grid
![Foto 3](https://link-3.jpg)
@end
```

Queda:

@grids grid-cols-3 gap-2
@grid
![Ejemplo](web/adjuntos/USBOTGSA/90757.avif)
@grid
![Conectando hub, teclado y raton](web/adjuntos/USBOTGSA/104954.avif)
@grid
![Ejemplo de uso](web/adjuntos/USBOTGSA/104964.avif)
@end

---

## 🎬 Videos y redes

Pega el enlace solo, en su propia linea. YouTube, TikTok, Facebook y Reddit se ven ahi mismo; Instagram, X y Threads quedan en un boton **▶ Ver post** para que la pagina cargue rapido. Sirven tambien los enlaces de "Compartir" de cada app. En medio de un texto queda como enlace comun.

Se escribe:
```
Mira como se usa:

https://youtu.be/stkw23ysF_Q
```

Queda:

Mira como se usa:

https://youtu.be/stkw23ysF_Q

---

## 📊 Tablas

Columnas separadas por **|**. La segunda linea, con guiones, separa los titulos. En celular, si no entra, se desliza de costado.

Se escribe:
```
| Talle | Pecho | Precio |
|---|---|---|
| S | 90 cm | 80.000 Gs |
| M | 96 cm | 85.000 Gs |
| L | 102 cm | 90.000 Gs |
```

Queda:

| Talle | Pecho | Precio |
|---|---|---|
| S | 90 cm | 80.000 Gs |
| M | 96 cm | 85.000 Gs |
| L | 102 cm | 90.000 Gs |

---

## 📋 Ficha tecnica

El dato en una linea y abajo **:** con el valor. Una linea en blanco entre dato y dato.

Se escribe:
```
Material
: Vidrio templado

Cantidad
: 6 vasos

Capacidad
: 350 ml
```

Queda:

Material
: Vidrio templado

Cantidad
: 6 vasos

Capacidad
: 350 ml

---

## 🪧 Carteles

Primera linea **> [!TIPO]** y el texto en las lineas siguientes, cada una empezando con **>**. Tipos: CONSEJO, NOTA, AVISO, PELIGRO. Una cita comun queda sin icono.

Se escribe:
```
> [!CONSEJO]
> Guarda la caja para la garantia.

> [!NOTA]
> Envios los martes y viernes.

> [!AVISO]
> Solo envios dentro de Asuncion.

> [!PELIGRO]
> No usar cerca del fuego.

> Cita comun.
```

Queda:

> [!CONSEJO]
> Guarda la caja para la garantia.

> [!NOTA]
> Envios los martes y viernes.

> [!AVISO]
> Solo envios dentro de Asuncion.

> [!PELIGRO]
> No usar cerca del fuego.

> Cita comun.

---

## ↔️ Alinear

Entre **::: center** (o right, left, justify) y **:::**.

Se escribe:
```
::: center
**Envio gratis**
desde 100.000 Gs
:::

::: right
Precios con IVA incluido
:::
```

Queda:

::: center
**Envio gratis**
desde 100.000 Gs
:::

::: right
Precios con IVA incluido
:::

---

## 🔽 Desplegable

Entre **::: details Titulo** y **:::**. Se abre al tocar el titulo.

Se escribe:
```
::: details Compatibilidad
Celulares con USB-C y OTG.
:::

::: details Envio
En el dia dentro de Asuncion.
:::
```

Queda:

::: details Compatibilidad
Celulares con USB-C y OTG.
:::

::: details Envio
En el dia dentro de Asuncion.
:::

---

## 🗂️ Pestanas

Entre **::: tabs** y **:::**, cada pestana empieza con **@tab Titulo**. Con **@tab:active** esa queda abierta al entrar; si no, la primera.

Se escribe:
```
::: tabs
@tab Descripcion
Adaptador de USB-C a USB-A.
@tab Compatibilidad
Celulares con USB-C y OTG.
@tab Envio
En el dia dentro de Asuncion.
:::
```

Queda:

::: tabs
@tab Descripcion
Adaptador de USB-C a USB-A.
@tab Compatibilidad
Celulares con USB-C y OTG.
@tab Envio
En el dia dentro de Asuncion.
:::

---

## 🙈 Texto oculto

Entre **!!** y **!!**. Se ve al pasar el mouse o tocarlo.

Se escribe:
```
Adivina la capital: !!Asuncion!!
```

Queda:

Adivina la capital: !!Asuncion!!

Ojo: dos signos de exclamacion pegados a lo que sigue (letra o signo) ocultan todo hasta los proximos dos. Esto no se ve:
```
!!NUEVO!!
```

Para exclamar deja siempre un espacio despues de los signos, asi: Oferta!! Solo hoy!! O usa la barra de **Simbolos tal cual**.

---

## 📌 Notas al pie

Las notas aparecen al final de la pagina. El numero lleva a la nota y la flecha vuelve.

Se escribe:
```
Garantia de 6 meses[^1].

[^1]: Solo defectos de fabrica, no golpes ni agua.
```

Queda:

Garantia de 6 meses[^1].

[^1]: Solo defectos de fabrica, no golpes ni agua.

---

## 🔣 Simbolos tal cual

Una barra **\\** justo antes de un simbolo lo muestra como es, sin formato.

Se escribe:
```
\*no es cursiva\* y \!!NUEVO\!!
```

Queda:

\*no es cursiva\* y \!!NUEVO\!!
