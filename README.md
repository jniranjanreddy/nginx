# nginx

## Source: https://www.youtube.com/watch?v=NwijBVfiK_o&t=4s

## What is nginx
```
server { #### Start of Context
		listen 80;   # Directive
		server_name 192.168.9.13;  # Directive
		root /bloggingtemplate;  # Directive

		location /contactus {
			return 200 "Hello!! you are inside the custom location";
		}
    } # End of Context
```
## Priority of Modifiers
```
1. Exact match                = URI
2. Preferential Prefic match  = ^~ URI
3. REGEX match                = ~* URI 
```
## variables
```
variables - NGINX configuration can hold the variable and NGINX variable can hold the String Value
set - directive is used to assign varibale in NGINX
set $a "Hello World"

Few important inbuilt variables
$args - List of arguments on the request line.
$body_bytes_sent - Number of bytes sent to the client.
$bytes_received  - Number of bytes received from a client.
$Connection_requests - Current number of requests made via connection
$date_local - Current time in the local time zone
$hostname - Host name
$nginx_version Shows nginx Version
```
## Rewrite and written
```
```
## Nginx Buffers.
```
client_body_buffer_size:
client_header_buffer_size:
timeouts:
gzip compression: 
```
## Siege
```
apt-get install siege
root# siege -v -r 2 -c 5 
```
## Nginx Dynamic Modules.
```
root@nginx02:~# cd /etc/nginx/
root@nginx02:/etc/nginx# ll
total 84
drwxr-xr-x   8 root root  4096 Jul 30 17:09 ./
drwxr-xr-x 132 root root 12288 Aug  1 11:59 ../
drwxr-xr-x   2 root root  4096 Nov 10  2022 conf.d/
-rw-r--r--   1 root root  1077 Feb  4  2019 fastcgi.conf
-rw-r--r--   1 root root  1007 Feb  4  2019 fastcgi_params
-rw-r--r--   1 root root  2837 Feb  4  2019 koi-utf
-rw-r--r--   1 root root  2223 Feb  4  2019 koi-win
-rw-r--r--   1 root root  3957 Feb  4  2019 mime.types
drwxr-xr-x   2 root root  4096 Nov 10  2022 modules-available/
drwxr-xr-x   2 root root  4096 Jul 29 22:45 modules-enabled/
-rw-r--r--   1 root root  2462 Aug  1 12:05 nginx.conf
-rw-r--r--   1 root root  1490 Jul 30 17:09 nginx.conf-backup
-rw-r--r--   1 root root   180 Feb  4  2019 proxy_params
-rw-r--r--   1 root root   636 Feb  4  2019 scgi_params
drwxr-xr-x   2 root root  4096 Jul 29 22:44 sites-available/
drwxr-xr-x   2 root root  4096 Jul 29 22:44 sites-enabled/
drwxr-xr-x   2 root root  4096 Jul 29 22:44 snippets/
-rw-r--r--   1 root root   664 Feb  4  2019 uwsgi_params
-rw-r--r--   1 root root  3071 Feb  4  2019 win-utf


root@nginx02:/etc/nginx# nginx -V
nginx version: nginx/1.18.0 (Ubuntu)
built with OpenSSL 1.1.1f  31 Mar 2020
TLS SNI support enabled
configure arguments: --with-cc-opt='-g -O2 -fdebug-prefix-map=/build/nginx-lUTckl/nginx-1.18.0=. -fstack-protector-strong -Wformat -Werror=format-security -fPIC -Wdate-time -D_FORTIFY_SOURCE=2' --with-ld-opt='-Wl,-Bsymbolic-functions -Wl,-z,relro -Wl,-z,now -fPIC' --prefix=/usr/share/nginx --conf-path=/etc/nginx/nginx.conf --http-log-path=/var/log/nginx/access.log --error-log-path=/var/log/nginx/error.log --lock-path=/var/lock/nginx.lock --pid-path=/run/nginx.pid --modules-path=/usr/lib/nginx/modules --http-client-body-temp-path=/var/lib/nginx/body --http-fastcgi-temp-path=/var/lib/nginx/fastcgi --http-proxy-temp-path=/var/lib/nginx/proxy --http-scgi-temp-path=/var/lib/nginx/scgi --http-uwsgi-temp-path=/var/lib/nginx/uwsgi --with-debug --with-compat --with-pcre-jit --with-http_ssl_module --with-http_stub_status_module --with-http_realip_module --with-http_auth_request_module --with-http_v2_module --with-http_dav_module --with-http_slice_module --with-threads --with-http_addition_module --with-http_gunzip_module --with-http_gzip_static_module --with-http_image_filter_module=dynamic --with-http_sub_module --with-http_xslt_module=dynamic --with-stream=dynamic --with-stream_ssl_module --with-mail=dynamic --with-mail_ssl_module

# How to install nginx modules.
apt-get install nginx-extras

# modules can be found here
/usr/lib/nginx/modules/ngx_http_image_filter_module.so


```

![image](https://user-images.githubusercontent.com/83489863/231879873-93719091-1340-4506-8250-9cbc0738e78d.png)

## nginx architecture
![image](https://user-images.githubusercontent.com/83489863/231884173-da2ef1d8-e102-48c1-a38c-6f8059db01a4.png)

BurpSuite for proxy testing
```
## Source
https://nginx.org/en/docs/http/request_processing.html
https://docs.nginx.com/nginx/admin-guide/web-server/web-server/

root@dev-server01:~# nginx -V
nginx version: nginx/1.18.0 (Ubuntu)
built with OpenSSL 1.1.1f  31 Mar 2020
TLS SNI support enabled
configure arguments: --with-cc-opt='-g -O2 -fdebug-prefix-map=/build/nginx-7KvRN5/nginx-1.18.0=. -fstack-protector-strong -Wformat -Werror=format-security -fPIC -Wdate-time -D_FORTIFY_SOURCE=2' --with-ld-opt='-Wl,-Bsymbolic-functions -Wl,-z,relro -Wl,-z,now -fPIC' --prefix=/usr/share/nginx --conf-path=/etc/nginx/nginx.conf --http-log-path=/var/log/nginx/access.log --error-log-path=/var/log/nginx/error.log --lock-path=/var/lock/nginx.lock --pid-path=/run/nginx.pid --modules-path=/usr/lib/nginx/modules --http-client-body-temp-path=/var/lib/nginx/body --http-fastcgi-temp-path=/var/lib/nginx/fastcgi --http-proxy-temp-path=/var/lib/nginx/proxy --http-scgi-temp-path=/var/lib/nginx/scgi --http-uwsgi-temp-path=/var/lib/nginx/uwsgi --with-debug --with-compat --with-pcre-jit --with-http_ssl_module --with-http_stub_status_module --with-http_realip_module --with-http_auth_request_module --with-http_v2_module --with-http_dav_module --with-http_slice_module --with-threads --with-http_addition_module --with-http_gunzip_module --with-http_gzip_static_module --with-http_image_filter_module=dynamic --with-http_sub_module --with-http_xslt_module=dynamic --with-stream=dynamic --with-stream_ssl_module --with-mail=dynamic --with-mail_ssl_module
root@dev-server01:~#


root@dev-server01:/etc/nginx/conf.d# nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful



```
### How to configure ssl or https
```
openssl req -x509  -days 365 -nodes -newkey rsa:2048 -keyout /etc/nginx/ssl/self.key -out /etc/nginx/ssl/self.crt
server {
        #listen 80;
        listen 443 ssl http2;
        server_name 192.168.9.13;
        ssl_certificate /etc/nginx/ssl/self.crt;
        ssl_certificate_key /etc/nginx/ssl/self.key;
            location / {
              proxy_set_header Host $host;
              proxy_pass http://appserver;
            }

    }
```

```
[root@k8s-helm nginx]# cat /etc/nginx/nginx.conf
# For more information on configuration, see:
#   * Official English Documentation: http://nginx.org/en/docs/
#   * Official Russian Documentation: http://nginx.org/ru/docs/

user nginx;
worker_processes auto;
error_log /var/log/nginx/error.log;
pid /run/nginx.pid;

# Load dynamic modules. See /usr/share/doc/nginx/README.dynamic.
include /usr/share/nginx/modules/*.conf;

events {
    worker_connections 1024;
}

http {
    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    access_log  /var/log/nginx/access.log  main;

    sendfile            on;
    tcp_nopush          on;
    tcp_nodelay         on;
    keepalive_timeout   65;
    types_hash_max_size 4096;

    include             /etc/nginx/mime.types;
    default_type        application/octet-stream;

    # Load modular configuration files from the /etc/nginx/conf.d directory.
    # See http://nginx.org/en/docs/ngx_core_module.html#include
    # for more information.
    include /etc/nginx/conf.d/*.conf;

    server {
        listen       80;
        listen       [::]:80;
        server_name  _;
        root         /usr/share/nginx/html;

        # Load configuration files for the default server block.
        include /etc/nginx/default.d/*.conf;

        error_page 404 /404.html;
        location = /404.html {
        }

        error_page 500 502 503 504 /50x.html;
        location = /50x.html {
        }
    }

# Settings for a TLS enabled server.
#
#    server {
#        listen       443 ssl http2;
#        listen       [::]:443 ssl http2;
#        server_name  _;
#        root         /usr/share/nginx/html;
#
#        ssl_certificate "/etc/pki/nginx/server.crt";
#        ssl_certificate_key "/etc/pki/nginx/private/server.key";
#        ssl_session_cache shared:SSL:1m;
#        ssl_session_timeout  10m;
#        ssl_ciphers HIGH:!aNULL:!MD5;
#        ssl_prefer_server_ciphers on;
#
#        # Load configuration files for the default server block.
#        include /etc/nginx/default.d/*.conf;
#
#        error_page 404 /404.html;
#            location = /40x.html {
#        }
#
#        error_page 500 502 503 504 /50x.html;
#            location = /50x.html {
#        }
#    }

}

```







## Name-based virtual servers
nginx first decides which server should process the request. Let’s start with a simple configuration where all three virtual servers listen on port *:80:

```
server {
    listen      80;
    server_name example.org www.example.org;
    ...
}

server {
    listen      80;
    server_name example.net www.example.net;
    ...
}

server {
    listen      80;
    server_name example.com www.example.com;
    ...
}
```
In this configuration nginx tests only the request’s header field “Host” to determine which server the request should be routed to. If its value does not match any server name, or the request does not contain this header field at all, then nginx will route the request to the default server for this port. In the configuration above, the default server is the first one — which is nginx’s standard default behaviour. It can also be set explicitly which server should be default, with the default_server parameter in the listen directive:
```
server {
    listen      80 default_server;
    server_name example.net www.example.net;
    ...
}
```
The default_server parameter has been available since version 0.8.21. In earlier versions the default parameter should be used instead.
Note that the default server is a property of the listen port and not of the server name. More about this later.

How to prevent processing requests with undefined server names
If requests without the “Host” header field should not be allowed, a server that just drops the requests can be defined:
```
server {
    listen      80;
    server_name "";
    return      444;
}
```
Here, the server name is set to an empty string that will match requests without the “Host” header field, and a special nginx’s non-standard code 444 is returned that closes the connection.

Since version 0.8.48, this is the default setting for the server name, so the server_name "" can be omitted. In earlier versions, the machine’s hostname was used as a default server name.
Mixed name-based and IP-based virtual servers
Let’s look at a more complex configuration where some virtual servers listen on different addresses:
```
server {
    listen      192.168.1.1:80;
    server_name example.org www.example.org;
    ...
}

server {
    listen      192.168.1.1:80;
    server_name example.net www.example.net;
    ...
}

server {
    listen      192.168.1.2:80;
    server_name example.com www.example.com;
    ...
}
```
In this configuration, nginx first tests the IP address and port of the request against the listen directives of the server blocks. It then tests the “Host” header field of the request against the server_name entries of the server blocks that matched the IP address and port. If the server name is not found, the request will be processed by the default server. For example, a request for www.example.com received on the 192.168.1.1:80 port will be handled by the default server of the 192.168.1.1:80 port, i.e., by the first server, since there is no www.example.com defined for this port.

As already stated, a default server is a property of the listen port, and different default servers may be defined for different ports:
```
server {
    listen      192.168.1.1:80;
    server_name example.org www.example.org;
    ...
}

server {
    listen      192.168.1.1:80 default_server;
    server_name example.net www.example.net;
    ...
}

server {
    listen      192.168.1.2:80 default_server;
    server_name example.com www.example.com;
    ...
}
```
A simple PHP site configuration
Now let’s look at how nginx chooses a location to process a request for a typical, simple PHP site:
```
server {
    listen      80;
    server_name example.org www.example.org;
    root        /data/www;

    location / {
        index   index.html index.php;
    }

    location ~* \.(gif|jpg|png)$ {
        expires 30d;
    }

    location ~ \.php$ {
        fastcgi_pass  localhost:9000;
        fastcgi_param SCRIPT_FILENAME
                      $document_root$fastcgi_script_name;
        include       fastcgi_params;
    }
}
```
nginx first searches for the most specific prefix location given by literal strings regardless of the listed order. In the configuration above the only prefix location is “/” and since it matches any request it will be used as a last resort. Then nginx checks locations given by regular expression in the order listed in the configuration file. The first matching expression stops the search and nginx will use this location. If no regular expression matches a request, then nginx uses the most specific prefix location found earlier.

Note that locations of all types test only a URI part of request line without arguments. This is done because arguments in the query string may be given in several ways, for example:

/index.php?user=john&page=1
/index.php?page=1&user=john
Besides, anyone may request anything in the query string:

/index.php?page=1&something+else&user=john
Now let’s look at how requests would be processed in the configuration above:

A request “/logo.gif” is matched by the prefix location “/” first and then by the regular expression “\.(gif|jpg|png)$”, therefore, it is handled by the latter location. Using the directive “root /data/www” the request is mapped to the file /data/www/logo.gif, and the file is sent to the client.
A request “/index.php” is also matched by the prefix location “/” first and then by the regular expression “\.(php)$”. Therefore, it is handled by the latter location and the request is passed to a FastCGI server listening on localhost:9000. The fastcgi_param directive sets the FastCGI parameter SCRIPT_FILENAME to “/data/www/index.php”, and the FastCGI server executes the file. The variable $document_root is equal to the value of the root directive and the variable $fastcgi_script_name is equal to the request URI, i.e. “/index.php”.
A request “/about.html” is matched by the prefix location “/” only, therefore, it is handled in this location. Using the directive “root /data/www” the request is mapped to the file /data/www/about.html, and the file is sent to the client.
Handling a request “/” is more complex. It is matched by the prefix location “/” only, therefore, it is handled by this location. Then the index directive tests for the existence of index files according to its parameters and the “root /data/www” directive. If the file /data/www/index.html does not exist, and the file /data/www/index.php exists, then the directive does an internal redirect to “/index.php”, and nginx searches the locations again as if the request had been sent by a client. As we saw before, the redirected request will eventually be handled by the FastCGI server.
written by Igor Sysoev
edited by Brian Mercer

```
#########################################################################
#ubuntu 

docker run -dit --name docker1 -p 8080:80 httpd:2.4
docker run -dit --name docker2 -p 8081:80 httpd:2.4

docker exec <container name> sed -i 's/It works!/Docker 1/' /usr/local/apache2/htdocs/index.html
docker exec <Container name> sed -i 's/It works!/Docker 2/' /usr/local/apache2/htdocs/index.html
    
cd /etc/nginx/sites-available
root@dev-server01 /etc/nginx/sites-available # cat docker1.jnrlabs.com
server {
  listen 80;
  server_name docker1.jnrlabs.com;

  location / {
    proxy_pass http://localhost:8080;
  }
}

root@dev-server01 /etc/nginx/sites-available # cat docker2.jnrlabs.com
server {
  listen 80;
  server_name docker2.jnrlabs.com;

  location / {
    proxy_pass http://localhost:8081;
  }
}
root@dev-server01 /etc/nginx/sites-available # ln -s /etc/nginx/sites-available/docker1.jnrlabs.com /etc/nginx/sites-enabled/
root@dev-server01 /etc/nginx/sites-available # ln -s /etc/nginx/sites-available/docker2.jnrlabs.com /etc/nginx/sites-enabled/

root@dev-server01 /etc/nginx/sites-enabled # ll
total 8
drwxr-xr-x 2 root root 4096 May 10 20:07 ./
drwxr-xr-x 8 root root 4096 May 10 21:11 ../
lrwxrwxrwx 1 root root   34 May 10 19:02 default -> /etc/nginx/sites-available/default
lrwxrwxrwx 1 root root   46 May 10 19:12 docker1.jnrlabs.com -> /etc/nginx/sites-available/docker1.jnrlabs.com
lrwxrwxrwx 1 root root   46 May 10 19:13 docker2.jnrlabs.com -> /etc/nginx/sites-available/docker2.jnrlabs.com
lrwxrwxrwx 1 root root   46 May 10 20:07 jenkins.jnrlabs.com -> /etc/nginx/sites-available/jenkins.jnrlabs.com
    
root@dev-server01 /etc/nginx/sites-available # nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
    
systemctl restart nginx

```
