#### psgsnodesecuexpressangl_note
######4 Prereq
[sample](https://github.com/clarkio/vulnerable-app)
######6
```
gulp serve-dev
```

######18
response headers (content policy 1.0)
```
content-security-policy: default-src 'self'; style-src 'self'; image-src 'self' http://loaclhost:8080;
```
IE:X-Content-Security-Policy

#####22
03:00 to run server (allow inline script)
```
gulp serve-dev --nosync  //run localhost:8001
```

######32 generate cert
```
openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365
```
######33 Impl
remove paraphrase we generated last clip
```
openssl rsa -in key.pem -out back.pem && mv back.pem key.pem
```
