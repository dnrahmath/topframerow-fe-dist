- [Back to Main README](../README.md)
- [Back to Main README Main Repo](../../../README.md)


# topframerow-fe-dist

####  [ 1 ] Copy & rename file sites-available (ASLI TETAP ADA)
```bash
cd /var/www/production/topframerow-fe-dist/server-conf
sudo cp sites-available.conf topframerow.my.id.conf
```

----------------------------------------

####  [ 2 ] Pindahkan file config ke Nginx
```bash
sudo mv topframerow.my.id.conf /etc/nginx/sites-available/
```

----------------------------------------

####  [ 3 ] setup NGINX
#####  [ 3.1 ] Hapus File Sebelumnya (JIKA ADA)
```bash
sudo rm /etc/nginx/sites-enabled/topframerow.my.id.conf
```

#####  [ 3.2 ] Aktifkan site
```bash
sudo ln -s /etc/nginx/sites-available/topframerow.my.id.conf \
           /etc/nginx/sites-enabled/
```

----------------------------------------

####  [ 4 ] Set permission agar bisa diakses website (jika sudah dilakukan sebelumnya-TIDAK PERLU)
```bash
sudo chown -R runner:web /var/www/production/topframerow-fe-dist
sudo chmod -R 755 /var/www/production/topframerow-fe-dist
```

----------------------------------------

####  [ 5 ] Test & reload Nginx
```bash
sudo nginx -t
sudo systemctl reload nginx
```

----------------------------------------

####  [ 6 ] Akses website || atau test dari dalam vps
```bash
runner@topframerow:~$ curl http://topframerow.my.id
runner@topframerow:~$ curl http://203.194.113.164
```

----------------------------------------
----------------------------------------

## Pasang SSL dalam vps

####  [ 7 ] INSTALL CERTBOT
```bash
sudo apt update
sudo apt install certbot python3-certbot-nginx -y
```

----------------------------------------

####  [ 8 ] GENERATE SSL
```bash
sudo certbot --nginx -d topframerow.my.id
```

- Saat prompt:
    - Email → isi email kamu
    - Agree → Y
    - Redirect HTTP → HTTPS → PILIH 2 (RECOMMENDED) ✅

- 👉 Certbot akan:
    - Pasang SSL
    - Tambah config HTTPS
    - Buat redirect otomatis HTTP → HTTPS

- ✅ HASIL AKHIR (AUTO DIBUAT CERTBOT)
    - Config kamu akan berubah jadi 2 server block:
    - 🔴 HTTP → HTTPS (AUTO REDIRECT)
    - 🔒 HTTPS

----------------------------------------

####  [ 9 ] TEST
```bash
sudo nginx -t
sudo systemctl reload nginx
```

----------------------------------------