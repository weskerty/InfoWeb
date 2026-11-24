Auto Instalable Termux para Reutilizar Android Viejito
https://github.com/got3nks/amutorrent

pkg install x11-repo tur-repo 
pkg update
pkg upgrade
pkg install wget nodejs-lts clang lld libc++ prowlarr transmission 
CXXFLAGS="-std=c++2a" npm install better-sqlite3@latest

cd server && CXXFLAGS="-std=c++2a" npm install  && cd ..         
npm install && npm run build && node server/server.js


### work
cd server && npm install-scripts approve --all && CXXFLAGS="-std=c++2a" npm install && cd .. && npm install-scripts approve --all && npm install && npm run build && node server/server.js



cd server && npm install-scripts approve --all && rm -rf node_modules/better-sqlite3 && CXXFLAGS="-std=c++2a" npm install && cd .. && npm install-scripts approve --all && npm install && npm run build && node server/server.js



iniciar transmision
transmission-daemon --config-dir aMuTorrent/conf/transmission

prowlarr --nobrowser --data=aMuTorrent/conf/prowlarr












## Screenshots

<details>
<summary>Desktop Screenshots</summary>

![Home](./docs/screenshots/home-desktop.png)
![Downloads](./docs/screenshots/downloads-desktop.png)
![Search](./docs/screenshots/search-desktop.png)

</details>

<details>
<summary>Mobile Screenshots</summary>

<div style="display: flex; gap: 10px; flex-wrap: wrap;">
  <img src="./docs/screenshots/home-mobile.png" height="400px" />
  <img src="./docs/screenshots/downloads-mobile.png" height="400px" />
  <img src="./docs/screenshots/search-mobile.png" height="400px" />
</div>

</details>