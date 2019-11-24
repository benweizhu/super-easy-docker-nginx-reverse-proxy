# super-easy-docker-nginx-reverse-proxy

1. Goto https://www.digitalocean.com/community/tools/nginx

2. Choose presets nodejs

3. Choose https disable(for now) 

4. Goto Server tab and put your server name

5. download and put under /nginx/config

6. comment out '# include /etc/nginx/conf.d/*.conf;' in nginx.conf

7. add web-upstream.conf to sites-enabled

```
upstream docker-web {
    server web:3000;
}
```

8. Change the proxy_pass to docker-web

```
# reverse proxy
location / {
    proxy_pass http://docker-web;
    include nginxconfig.io/proxy.conf;
}
```

You mean want to know what does upstream do why it works.

http://nginx.org/en/docs/http/ngx_http_upstream_module.html

https://docs.docker.com/compose/networking/