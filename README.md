<p>Untuk aaPanel Docker Deployment di CasaOS, Anda bisa memilih untuk menggunakan Docker CLI.</p>

1. Menggunakan Docker CLI (Command Line Interface)
Jika Anda ingin menjalankan aaPanel langsung dari terminal menggunakan Docker CLI, Anda bisa mengikuti perintah yang sudah saya berikan sebelumnya:

Langkah-langkah:
<li>Masuk ke appstore casaos, dan klik custom install lalu klik icon terminal.</li>
<li>Copy kode di bawah ini dan Jalankan aaPanel menggunakan Docker CLI, bukan docker compose, lalu klik submit.</li>

```bash
docker run -d -p 8886:7800 -p 22:21 -p 443:443 -p 80:80 -p 889:888 -v ~/website_data:/www/wwwroot -v ~/mysql_data:/www/server/data -v ~/vhost:/www/server/panel/vhost aapanel/aapanel:lib
  ```
