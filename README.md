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
