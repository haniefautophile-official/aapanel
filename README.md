<p>Untuk aaPanel Docker Deployment di CasaOS, Anda bisa memilih untuk menggunakan Docker CLI.</p>

1. Menggunakan Docker CLI (Command Line Interface)
Jika Anda ingin menjalankan aaPanel langsung dari terminal menggunakan Docker CLI, Anda bisa mengikuti perintah yang sudah saya berikan sebelumnya:

Langkah-langkah:
<li>Masuk ke appstore casaos, dan klik custom install lalu klik icon terminal.</li>
<li>Copy kode di bawah ini dan Jalankan aaPanel menggunakan Docker CLI, bukan docker compose, lalu klik submit.</li>

```bash
docker run -d \
  -p 8886:7800 \      # Port untuk akses panel kontrol
  -p 2222:21 \        # Ganti port SSH menjadi 2222
  -p 443:443 \        # Port untuk HTTPS
  -p 8080:80 \        # Ubah port HTTP dari 80 ke 8080
  -p 889:888 \        # PhpMyAdmin access
  -v ~/website_data:/www/wwwroot \   # Direktori untuk data website
  -v ~/mysql_data:/www/server/data \ # Direktori untuk data MySQL
  -v ~/vhost:/www/server/panel/vhost \ # Direktori untuk file vhost
  aapanel/aapanel:lib
  ```
