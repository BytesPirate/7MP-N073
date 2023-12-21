
## nginx location 配置

### 基本配置

文件位置：`/etc/nginx/conf/conf.d/xxx.conf` or `/usr/local/nginx1.25/conf/conf.d/xxx.conf`

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