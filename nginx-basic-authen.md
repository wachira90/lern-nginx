# Restricting Access with HTTP Basic Authentication

install by command 
```
yum install nginx-all-modules -y
```

## Debian, Ubuntu) 
```
apt install apache2-utils -y
```

## RHEL/CentOS/Oracle Linux) is installed
```
yum install httpd-tools -y
```

## Create a password file and a first user. Run the htpasswd utility with the -c flag (to create a new file), the file pathname as the first argument, and the username as the second argument:


apache2 file => /etc/apache2/.htpasswd

nginx file => /etc/nginx/.htpasswd

```
sudo htpasswd -c /etc/nginx/.htpasswd user1
```
## Create additional user-password pairs. Omit the -c flag because the file already exists:

```
sudo htpasswd /etc/nginx/.htpasswd user2
```

## cat /etc/nginx/.htpasswd
```
[root@logserver ~]# cat /etc/nginx/.htpasswd
admininno:$apr1$qm0BWTOA$8qpg400kv3Sf88kpuGOgL/
superadmin:$apr1$KP2BeDbF$0NNvPpE/WiGkZei59o/pA0
[root@logserver ~]#
```

## add config
```
location /api {
    auth_basic           “Administrator’s Area”;
    auth_basic_user_file /etc/nginx/.htpasswd; 
}
```


Alternatively, you you can limit access to the whole website with basic authentication but still make some website areas public. In this case, specify the off parameter of the auth_basic directive that cancels inheritance from upper configuration levels:

```
server {
    ...
    auth_basic           "Administrator’s Area";
    auth_basic_user_file /etc/nginx/.htpasswd;

    location /public/ {
        auth_basic off;
    }
}
```
