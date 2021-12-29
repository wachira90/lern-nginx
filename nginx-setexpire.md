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
