# on windows config

## start nginx bat file

```
@ECHO OFF
@ECHO START NGINX1.20.0
START C:\nginx-1.20.0\nginx.exe
REM C:\nginx-1.20.0\bin\RunHiddenConsole.exe C:\nginx-1.20.0\php-7.3.28\php-cgi.exe -b 127.0.0.1:9123 -C C:\nginx-1.20.0\php-7.3.28\php.ini
START C:\nginx-1.20.0\bin\RunHiddenConsole.exe C:\nginx-1.20.0\php-7.3.28\php-cgi.exe -b 9123 -C C:\nginx-1.20.0\php-7.3.28\php.ini
ECHO THIS WINDOWS CLOSE AUTO
TIMEOUT /T 3
```

## stop nginx bat file

```
@ECHO OFF
@ECHO STOP NGINX1.16.1
TASKKILL /F /IM php-cgi.exe
TASKKILL /F /IM nginx.exe
REM START C:\nginx-1.16.1\nginx.exe -s quit
TIMEOUT /T 3
```


## show process running

```
@ECHO OFF
@ECHO SHOW PROCESS
tasklist /fi "imagename eq nginx.exe"
tasklist /fi "imagename eq php-cgi.exe"
REM PAUSE
TIMEOUT /T 5
```

## add php 

```
location ~ \.php$ {
    fastcgi_pass localhost:9000;
    fastcgi_index index.php;
    fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    include fastcgi_params;
}
```
