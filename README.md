# NGINX
```
upstream web {
    server web:8000;
}

server {

    listen 80;
    server_name 149.154.64.149;

    client_max_body_size 4G;

    location / {
        proxy_pass http://web;
        proxy_redirect off;
        proxy_set_header Host $http_host;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }

    location /staticfiles/ {
        alias  /root/gangx-docker-nginx/staticfiles/; # путь до staticfiles
    }

    location /media/ {
        alias /root/gangx-docker-nginx/media/; # путь до media
    }
}
```
