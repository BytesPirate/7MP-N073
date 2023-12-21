
## nginx location 配置

### 基本配置

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

### 其他配置

1. 上传文件
	```nginx config
location ^~ /uploads {
    alias /data/uploads;   
}
	```