# nginx set limit upload

Source: http://www.cyberciti.biz/faq/linux-unix-bsd-nginx-413-request-entity-too-large/

## Edit the conf file of nginx:

```
nano /etc/nginx/nginx.conf
```

## Add a line in the http section:

```
http {
    client_max_body_size 100M;
}
```

## use MB it will not work, only the M! and restart nginx

```
systemctl restart nginx
```
