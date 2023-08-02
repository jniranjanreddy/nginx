## Client Cacheing
```
Client Cacheing - web servers do not control Client-side cacheing to full extent, obviously,
but they may issue recommendations what to cache and how, in the form of special HTTP response headers.
```
### Cache-Control-Header
```
This is the most important Header to set it effectively 'switches on' caching in the browser.
Without this header the browser will re-request the file on each subsequent request.

1. Cache-Control:public
2. Cache-Control:private
3. Cache-Control:public, max-age=31536000   # age should be in seconds
4. Cache-Control: Expires - age should be in date.
5. If Expires and max-age is used which will precedence.  (Note: max-age takes precedence)
```
### Gzip compression
```
root@nginx02:~# curl -I http://192.168.9.13/assets/css/bootstrap.min.css
HTTP/1.1 200 OK
Server: nginx/1.18.0 (Ubuntu)
Date: Wed, 02 Aug 2023 12:54:53 GMT
Content-Type: text/css
Content-Length: 47
Connection: keep-alive
Expires: Sun, 01 Oct 2023 12:54:53 GMT
Cache-Control: max-age=5184000
Cache-Control: public
Pragma: Public
Vary: Accept-Encoding
Company: NiruLabs


root@nginx02:~# curl -H "Accept-Encoding: gzip, deflate" -I http://192.168.9.13/assets/css/bootstrap.min.css
HTTP/1.1 200 OK
Server: nginx/1.18.0 (Ubuntu)
Date: Wed, 02 Aug 2023 12:57:11 GMT
Content-Type: text/css
Connection: keep-alive
Expires: Sun, 01 Oct 2023 12:57:11 GMT
Cache-Control: max-age=5184000
Cache-Control: public
Pragma: Public
Vary: Accept-Encoding
Company: NiruLabs
Content-Encoding: gzip  # Here we can see the Gzip Compression.
```
## Micro caching
```

```
## ssl
```

```

