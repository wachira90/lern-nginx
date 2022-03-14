# Testing

## Get Requests count per IP per request in Nginx access.log
````
grep '12/Jan/2021' access.log | awk '{print $1}' | sort | uniq -c | sort -nr
````

## Certain date using extended regular expression

````
grep -E '11/Jan/2021|12/Jan/2021' access.log | awk '{print $1}' | sort | uniq -c | sort -nr | head -20

grep '09/Mar/2022' access.log.txt | awk '{print $1}' | sort | uniq -c | sort -nr

grep -E '01/Mar/2022|09/Mar/2022' access.log | awk '{print $1}' | sort | uniq -c | sort -nr | head -20
````
