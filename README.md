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

34 wireshark
http filter:
```
http.host contains "localhost"
```
https filter:
```
tcp.port==8001
```
######38
automatic submit form:
```
document.forms[0].submit();
```
######41 Attack prevention
Header checks, Synchonizer token pattern.

######46 Synchronizer example
1 user request a login, server receive that request.  
2 server create a session fot that user for a reference for subsequence request from this user  
3 response the resource we requeted  
4 user request profile resource from server  
5 server generate form with CSRF token using the user's session  
6 response back with CSRF token
7 User change the profile, request change with token  
8 server validate CSRF token, if valid, then process change  


######53 Attack
```
<style>
iframe{
  width:100px;
  height:100px;
  position:absolute;
  top:0;
  left:0;
  opacity:0;
}
</style>
<button style="z-index:-1;">click here</button>
<iframe src="https://" width="400" height="800"></iframe>
```
######56 Prevention with HTTP header
X-FRAME-OPTIONS  
[mozilla doc](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options)
```
DENY:The browser will deny any attempts to load any sites from iframe
SAMEORIGIN
ALLOW-FROM uri    //means that site `uri` can load iframe of this site.
```
