# 不同项目的nginx配置文件

文件位置：/etc/nginx/conf/conf.d/xxx.conf

## vue 项目

```nginx config
server {
    listen 80;
    server_name example.14bytes.com;
    
    location /example {
        alias /data/xxx/xxx/example-14byes/dist;
        index index.html index.htm;
        try_files $uri $uri/ /example/index.html;
    }
}
```

## java 项目

```nginx config
server {
    listen 80;
    server_name example.14bytes.com;
    
    location ^~ /example-api {
        proxy_pass http://127.0.0.1:8080;
        proxy_headers_hash_max_size 51200;
        proxy_headers_hash_bucket_size 6400;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```

配置上传

```nginx config
location ^~ /uploads {
    alias /data/uploads;   
}
```

## php 项目

```nginx config
server {
    listen 80;
    server_name example.14bytes.com;
    
    location ~ \.php$ {
        root    /data/xxx/xxx/web;
        fastcgi_pass    127.0.0.1:9073;
        fastcgi_index   index.php;
        fastcgi_param   SCRIPT_FILENAME     $document_root$fastcgi_script_name;
        include         fastcgi_params;
    }
    
    location / {
        root    /data/xxx/xxx/web；
        index   index.php;
        try_files   $uri $uri/ /index.php?$query_string;
    }
}
```