- [Back to Main README](../README.md)
- [Back to Main README Main Repo](../../../README.md)


####  [ 1 ] Berpindah Directory
```bash
C:\Users\dnrahmath>cd /d D:\file-kodingan
```

----------------------------------------

####  [ 2 ] Menjalankan App
```bash
D:\file-kodingan>
  npm create vite@latest topframerow-fe -- --template react-ts
  cd topframerow-fe
  npm install
  npm run dev
```

----------------------------------------

####  [ 3 ] install tailwinds
https://tailwindcss.com/docs/installation/using-vite
```bash
npm install tailwindcss @tailwindcss/vite
```
dan ikuti selanjutnya

----------------------------------------

####  [ 4 ] Gunakan Sertifikat SSL Custom (Untuk Produksi atau Penggunaan Tetap)
**Alternatif** : Jika kamu tidak ingin menginstall OpenSSL secara manual, gunakan mkcert (lebih mudah dan tanpa error keamanan di browser):
```bash
npm install --save-dev vite-plugin-mkcert
```

_D:\topframerow-fe\vite.config.ts_
```js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'
import mkcert from 'vite-plugin-mkcert';
import tailwindcss from '@tailwindcss/vite'

// https://vite.dev/config/
export default defineConfig({
  plugins: [
    react(), 
    mkcert(),
    tailwindcss(),
  ], // Tambahkan mkcert ke plugins
  server: {
    https: true, // Aktifkan HTTPS
  },
});

//D:\topframerow-fe\src\index.css
@import "tailwindcss";
```

----------------------------------------

####  [ 5 ] Install Package

```bash
PS D:\topframerow-fe> npm install --save-dev react-router-dom
PS D:\topframerow-fe> npm install --save-dev html5-qrcode
PS D:\topframerow-fe> npm install --save-dev del-cli

PS D:\topframerow-fe> npm install --save-dev lucide-react
PS D:\topframerow-fe> npm install --save-dev @headlessui/react react-world-flags 

PS D:\topframerow-fe> npm install --save-dev react-colorful

npm install three @react-three/fiber @react-three/drei
npm install jszip
```

----------------------------------------

####  [ 6 ] Proses Develop and BUILD - **[ _✎ INI PENTING_ ]** -

```bash
npm cache clean --force
npm run dev
```

memindahkan seluruh asset yang berada pada 

> **<u>repo-fe/public</u>** ke **<u>repo-fe/dist</u>/topframerow-fe-dist/public**


- [list Command **package.json**](../../../package.json)

```js
/*
<u> npm run prepare-gh </u>
sudah diwakilkan pada
"npm run predeploy"
*/
npm run prepare-gh
```

**[ BUILD ]**

proses pengembangan lakuakn dibawah untuk panggil function pada package.json -> scripts

```js
/*
lakukan edit (.env) dahulu sebelum build , karena ini menentukan
*/
```

```bash
npm run predeploy
npm run push-deploy
```

```js
/*
<u> npm run commit-private </u>
bisa di Commit pakai UI addons Visual Code
"Souce Control (Ctrl+Shift+G)"
*/
npm run commit-private
```


**[ Masuk Kedalam VPS dan ke repo _"topframerow-fe-dist"_ ]**


####  Pindah ke VPS Server dan Masuk Directory Repository Hasil Build

 - SESUAIKAN
```bash
runner@topframerow:~$ cd /var/www/production/topframerow-fe-dist
```

```bash
make force-pull-production
```

----------------------------------------

####  [ 7 ] Memperbaiki Package

```bash
Remove-Item -Recurse -Force node_modules, package-lock.json
Remove-Item -Recurse -Force node_modules, package-lock.json, dist, .vite
```

Install kembali

```bash
npm install

npm install tailwindcss @tailwindcss/postcss postcss autoprefixer
npm install -D stylelint stylelint-config-standard stylelint-config-tailwindcss

//npm install -D tailwindcss@latest
```

----------------------------------------