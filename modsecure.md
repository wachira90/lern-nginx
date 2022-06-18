# modsecure

## clone repo
````
cd /etc/nginx/
git clone https://github.com/SpiderLabs/owasp-modsecurity-crs.git
````

## add config
````
location / {
    modsecurity on;
    modsecurity_rules_file /etc/nginx/modsec/main.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/crs-setup.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-901-INITIALIZATION.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-903.9001-DRUPAL-EXCLUSION-RULES.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-903.9002-WORDPRESS-EXCLUSION-RULES.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-903.9003-NEXTCLOUD-EXCLUSION-RULES.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-903.9004-DOKUWIKI-EXCLUSION-RULES.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-903.9005-CPANEL-EXCLUSION-RULES.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-903.9006-XENFORO-EXCLUSION-RULES.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-905-COMMON-EXCEPTIONS.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-910-IP-REPUTATION.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-911-METHOD-ENFORCEMENT.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-912-DOS-PROTECTION.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-913-SCANNER-DETECTION.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-920-PROTOCOL-ENFORCEMENT.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-921-PROTOCOL-ATTACK.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-930-APPLICATION-ATTACK-LFI.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-931-APPLICATION-ATTACK-RFI.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-932-APPLICATION-ATTACK-RCE.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-933-APPLICATION-ATTACK-PHP.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-934-APPLICATION-ATTACK-NODEJS.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-941-APPLICATION-ATTACK-XSS.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-942-APPLICATION-ATTACK-SQLI.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-943-APPLICATION-ATTACK-SESSION-FIXATION.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-944-APPLICATION-ATTACK-JAVA.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/REQUEST-949-BLOCKING-EVALUATION.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/RESPONSE-950-DATA-LEAKAGES.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/RESPONSE-951-DATA-LEAKAGES-SQL.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/RESPONSE-952-DATA-LEAKAGES-JAVA.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/RESPONSE-953-DATA-LEAKAGES-PHP.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/RESPONSE-954-DATA-LEAKAGES-IIS.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/RESPONSE-959-BLOCKING-EVALUATION.conf;
    modsecurity_rules_file /etc/nginx/owasp-modsecurity-crs/rules/RESPONSE-980-CORRELATION.conf;
    error_log /var/log/nginx/modsec.log;
    root   /usr/share/nginx/html;
    index  index.html index.htm;
}
````
