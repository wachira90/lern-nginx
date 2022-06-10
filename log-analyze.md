# log analyze

## nano genanalyze.sh

````
#!/bin/bash

# variables
LOGFILE="/var/log/nginx/access.log"
LOGFILE_GZ="/var/log/nginx/access.log.*"
RESPONSE_CODE="200"

# functions
filters(){
grep $RESPONSE_CODE \
| grep -v "\/rss\/" \
| grep -v robots.txt \
| grep -v "\.css" \
| grep -v "\.jss*" \
| grep -v "\.png" \
| grep -v "\.ico"
}

filters_404(){
grep "404"
}

request_ips(){
awk '{print $1}'
}

request_method(){
awk '{print $6}' \
| cut -d'"' -f2
}

request_pages(){
awk '{print $7}'
}

wordcount(){
sort \
| uniq -c
}

sort_desc(){
sort -rn
}

return_kv(){
awk '{print $1, $2}'
}

request_pages(){
awk '{print $7}'
}

return_top_ten(){
head -10
}

## actions
get_request_ips(){
echo ""
echo "Top 10 Request IP's:"
echo "===================="

cat $LOGFILE \
| filters \
| request_ips \
| wordcount \
| sort_desc \
| return_kv \
| return_top_ten
echo ""
}

get_request_methods(){
echo "Top Request Methods:"
echo "===================="
cat $LOGFILE \
| filters \
| request_method \
| wordcount \
| return_kv
echo ""
}

get_request_pages_404(){
echo "Top 10: 404 Page Responses:"
echo "==========================="
zgrep '-' $LOGFILE $LOGFILE_GZ\
| filters_404 \
| request_pages \
| wordcount \
| sort_desc \
| return_kv \
| return_top_ten
echo ""
}


get_request_pages(){
echo "Top 10 Request Pages:"
echo "====================="
cat $LOGFILE \
| filters \
| request_pages \
| wordcount \
| sort_desc \
| return_kv \
| return_top_ten
echo ""
}

get_request_pages_all(){
echo "Top 10 Request Pages from All Logs:"
echo "==================================="
zgrep '-' --no-filename $LOGFILE $LOGFILE_GZ \
| filters \
| request_pages \
| wordcount \
| sort_desc \
| return_kv \
| return_top_ten
echo ""
}

# executing
get_request_ips
get_request_methods
get_request_pages
get_request_pages_all
get_request_pages_404
````

# permission
````
sudo chmod +x genanalyze.sh
````

# run
````
./genanalyze.sh
````

# result
````
[root@srv11 ~]# nano genparse.sh
[root@srv11 ~]# chmod +x genparse.sh
[root@srv11 ~]# ./genparse.sh

Top 10 Request IP's:
====================
1265664 172.31.164.9

Top Request Methods:
====================
20262 GET
1245435 POST

Top 10 Request Pages:
=====================
1245408 /api/graphql
14608 /"
525 /static/media/Kanit-Regular.b935eb67.ttf
497 /static/media/Kanit-Light.3a5af915.ttf
494 /static/media/Kanit-Medium.79d3ce8b.ttf
477 /static/media/thsarabunnew-webfont.940b7d99.woff
454 /static/media/Kanit-SemiBold.80243544.ttf
452 /static/media/Kanit-Italic.dc367df0.ttf
442 /static/media/fa-regular-400.4a74738e.woff2
440 /static/media/fa-solid-900.8e1ed89b.woff2

Top 10 Request Pages from All Logs:
===================================
gzip: --no-filename.gz: No such file or directory
gzip: /var/log/nginx/access.log.*.gz: No such file or directory
1245461 /api/graphql
14609 /"
525 /static/media/Kanit-Regular.b935eb67.ttf
497 /static/media/Kanit-Light.3a5af915.ttf
494 /static/media/Kanit-Medium.79d3ce8b.ttf
477 /static/media/thsarabunnew-webfont.940b7d99.woff
454 /static/media/Kanit-SemiBold.80243544.ttf
452 /static/media/Kanit-Italic.dc367df0.ttf
442 /static/media/fa-regular-400.4a74738e.woff2
440 /static/media/fa-solid-900.8e1ed89b.woff2

Top 10: 404 Page Responses:
===========================
gzip: /var/log/nginx/access.log.*.gz: No such file or directory
5154 /api/graphql
26 /manifest.json
7 /static/media/Kanit-Italic.dc367df0.ttf
7 /api/gettbllock
5 /static/media/Kanit-Regular.b935eb67.ttf
4 /static/media/thsarabunnew-webfont.940b7d99.woff
4 /static/media/thsarabunnew_bold-webfont.8d8146f0.woff
4 /static/media/Kanit-Medium.79d3ce8b.ttf
4 /static/media/Kanit-Light.3a5af915.ttf
4 /static/media/fa-solid-900.8e1ed89b.woff2

[root@srv11 ~]#

````
