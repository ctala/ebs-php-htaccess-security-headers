# ebs-php-htaccess-security-headers

Example of Security Headers for a PHP application using Elastic Beanstalk

This example add the .htaccess file to AWS PHP Example for Elastic Beanstalk.

```
# Extra Security Headers
<IfModule mod_headers.c>
	Header set X-XSS-Protection "1; mode=block"
	Header always append X-Frame-Options SAMEORIGIN
	Header set X-Content-Type-Options nosniff
</IfModule>
```

## Nikto Vulnerability Scanner

### Before Htaccess File

```
root@kali:~# nikto -host http://XXXXXXXXXX.gqq2ap6cxr.us-west-2.elasticbeanstalk.com
- Nikto v2.1.6
---------------------------------------------------------------------------
+ Target IP:          XX.XX.XX.XX
+ Target Hostname:    XXXXXXXXXX.gqq2ap6cxr.us-west-2.elasticbeanstalk.com
+ Target Port:        80
+ Start Time:         2019-12-14 14:32:49 (GMT-5)
---------------------------------------------------------------------------
+ Server: Apache
+ The anti-clickjacking X-Frame-Options header is not present.
+ The X-XSS-Protection header is not defined. This header can hint to the user agent to protect against some forms of XSS
+ The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type

```

### After Htaccess File

```
root@kali:~nikto -host http://XXXXXXXXXX.gqq2ap6cxr.us-west-2.elasticbeanstalk.com
- Nikto v2.1.6
---------------------------------------------------------------------------
+ Target IP:          XX.XX.XX.XX
+ Target Hostname:    XXXXXXXXXX.gqq2ap6cxr.us-west-2.elasticbeanstalk.com
+ Target Port:        80
+ Start Time:         2019-12-14 14:47:15 (GMT-5)
---------------------------------------------------------------------------
+ Server: Apache
+ No CGI Directories found (use '-C all' to force check all possible dirs)

```