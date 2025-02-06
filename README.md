docker run -d \
  -p 8886:7800 \      # Panel control access
  -p 22:21 \          # SSH access
  -p 443:443 \        # HTTPS access
  -p 80:80 \          # HTTP access
  -p 889:888 \        # PhpMyAdmin access
  -v ~/website_data:/www/wwwroot \   # Mount directory for website data
  -v ~/mysql_data:/www/server/data \ # Mount directory for MySQL data
  -v ~/vhost:/www/server/panel/vhost \ # Mount directory for vhost files
  aapanel/aapanel:lib  # Docker image tag, use `lib` for faster installation
