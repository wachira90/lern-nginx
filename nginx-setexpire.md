# set expire ico
````
location = /favicon.ico {
    log_not_found   off;
    access_log  off;
}
````

````
location ~*  \.(jpg|jpeg|png|gif|ico|css|js)$ {
    expires 365d;
}
````

````
location ~* \.(ico|css|js|gif|jpe?g|png)(\?[0-9]+)?$ {
    expires max;
    log_not_found off;
}
````
