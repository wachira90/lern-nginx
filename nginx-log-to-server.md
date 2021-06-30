# nginx log to server

http://techies-world.com/configure-nginx-to-send-logs-to-rsyslog/
```
nano /etc/nginx/nginx.conf
```

add this

```
error_log syslog:server=unix:/dev/log,facility=local7,tag=nginx,severity=error;
access_log syslog:server=unix:/dev/log,facility=local7,tag=nginx,severity=info main;
```

Step1: Open the rsyslog config file  (line 34)

```
nano /etc/rsyslog.conf
```

Step2: Add the following line before the line => $IncludeConfig /etc/rsyslog.d/*.conf
```
$ModLoad imfile
```
Step3: Create a new file for nginx rsyslog configuration
```
nano /etc/rsyslog.d/nginx.conf
```
Step4: Update the following lines.
```
# error log
$InputFileName /var/log/nginx/error.log
$InputFileTag nginx:
$InputFileStateFile stat-nginx-error
$InputFileSeverity error
$InputFileFacility local6
$InputFilePollInterval 1
$InputRunFileMonitor

# access log
$InputFileName /var/log/nginx/access.log
$InputFileTag nginx:
$InputFileStateFile stat-nginx-access
$InputFileSeverity notice
$InputFileFacility local6
$InputFilePollInterval 1
$InputRunFileMonitor
```

Step5: Restart rsyslog nginx service
```
systemctl restart nginx rsyslog

```

## Tip:

nano /etc/rsyslog.conf

```
##### UDP:

    *.* @graylog.example.org:514;RSYSLOG_SyslogProtocol23Format

##### TCP:

    *.* @@graylog.example.org:514;RSYSLOG_SyslogProtocol23Format
```
