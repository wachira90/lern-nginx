# lern-nginx
lern-nginx

## port 80 redirect 443

````
server {
    listen 80;
    listen [::]:80;
    server_name  localhost;
    return 301 https://$host$request_uri;
}    
````

## add php
````
location ~ \.php$ {
    try_files $uri =404;
    fastcgi_split_path_info ^(.+\.php)(/.+)$;
    fastcgi_pass localhost:9123;
    fastcgi_index index.php;
    include fastcgi_params;
    fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
}
````
## set expire
````
# Browser caching of static assets.
location ~* \.(jpg|jpeg|png|gif|ico|css|js|pdf)$ {
expires 7d;
add_header Cache-Control "public, no-transform";
}

# Media: images, icons, video, audio send expires headers
location ~* \.(?:jpg|jpeg|gif|png|ico|cur|gz|svg|svgz|mp4|ogg|ogv|webm)$ {
  expires 1M;
  access_log off;
  add_header Cache-Control "public";
}

# Web fonts send expires headers
location ~* \.(?:eot|otf|ttf|woff|woff2)$ {
  expires 3M;
  access_log off;
  add_header Cache-Control "public";
}

# CSS and Javascript send expires headers.
location ~* \.(?:css|js)$ {
  expires 1y;
  access_log off;
  add_header Cache-Control "public";
}

# HTML send expires headers.
location ~* \.(html)$ {
  expires 7d;
  access_log off;
  add_header Cache-Control "public";
}
````
