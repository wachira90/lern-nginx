# block access from ip

````
server {
    listen    80;
    listen    443 ssl;
    server_name 172.16.1.5;
    location / {
        deny all;
    }
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_prefer_server_ciphers on;
    ssl_ciphers ECDHE+RSAGCM:ECDH+AESGCM:DH+AESGCM:ECDH+AES256:DH+AES256:ECDH+AES128:DH+AES:!aNULL!eNull:!EXPORT:!DES:!3DES:!MD5:!DSS;
    ssl_certificate /etc/nginx/ssl/server.crt;
    ssl_trusted_certificate /etc/nginx/ssl/server.crt;
    ssl_certificate_key /etc/nginx/ssl/server.key;
}
````
