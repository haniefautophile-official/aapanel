<p>Untuk aaPanel Docker Deployment di CasaOS, Anda bisa memilih untuk menggunakan Docker CLI.</p>

<li>Menggunakan Docker CLI (Command Line Interface)</li>
Jika Anda ingin menjalankan aaPanel langsung dari terminal menggunakan Docker CLI, Anda bisa mengikuti perintah yang sudah saya berikan sebelumnya:

<li>Langkah-langkah:</li>
<li>Masuk ke appstore casaos, dan klik custom install lalu klik icon import di pojok kanan atas.</li>
<li>Copy kode di bawah ini dan Jalankan aaPanel menggunakan Docker CLI, bukan docker compose, lalu klik submit.</li>

```bash
version: '3.8'

services:
  aapanel:
    container_name: aapanel
    image: aapanel/aapanel:lnmp
    restart: always
    privileged: true
    ports:
      - "8886:7800"  # Port akses aaPanel
      - "22:21"      # Port FTP
      - "443:443"    # Port HTTPS
      - "80:80"      # Port HTTP
      - "889:888"    # Port tambahan
    environment:
      - TZ=Asia/Jakarta
    volumes:
      - ~/website_data:/www/wwwroot
      - ~/mysql_data:/www/server/data
      - ~/vhost:/www/server/panel/vhost

  nginx:
    container_name: nginx
    image: nginx:latest
    restart: always
    ports:
      - "80:80"  # HTTP
      - "443:443"  # HTTPS
    volumes:
      - ~/website_data:/www/wwwroot
      - ./nginx/conf.d:/etc/nginx/conf.d
    depends_on:
      - php

  php:
    container_name: php-fpm
    image: php:8.2-fpm
    restart: always
    volumes:
      - ~/website_data:/www/wwwroot
    depends_on:
      - mariadb

  mariadb:
    container_name: mariadb
    image: mariadb:latest
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: rootpass
      MYSQL_DATABASE: mydatabase
      MYSQL_USER: myuser
      MYSQL_PASSWORD: mypassword
    volumes:
      - ~/mysql_data:/var/lib/mysql

  phpmyadmin:
    container_name: phpmyadmin
    image: phpmyadmin/phpmyadmin:latest
    restart: always
    ports:
      - "8080:80"  # Akses phpMyAdmin melalui browser
    environment:
      - PMA_HOST=mariadb
      - PMA_PORT=3306
      - PMA_ARBITRARY=1
    depends_on:
      - mariadb

  ```
<li>Akses aapanel di browser menggunakan alamat http://youripaddress:8886/⁠aapanel</li>

```bash
Default installation entry:aapanel
Default username:aapanel
Default password:aapanel123
Default root password:aapanel123
```
