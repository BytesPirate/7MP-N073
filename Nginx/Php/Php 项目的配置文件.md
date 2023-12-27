## nginx location

### 基本配置

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

	location ~ ^/(api|admin/api) {
		root    /data/xxx/xxx/web;
		index   index.php;
		try_files    $uri  $uri/  /index.php$is_args$args;
	}

    location / {
        root    /data/xxx/xxx/web；
        index   index.php;
        try_files   $uri $uri/ /index.php?$query_string;
    }
}
```

## Php 文件挂载

```nginx config
location /attaches/file {
	alias    /data/attaches/[php-project-name]
}
```