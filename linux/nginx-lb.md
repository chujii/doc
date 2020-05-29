

**nginx的负载均衡有4种模式：**

1)、轮询（默认） 
每个请求按时间顺序逐一分配到不同的后端服务器，如果后端服务器down掉，能自动剔除。 
2)、weight 
指定轮询几率，weight和访问比率成正比，用于后端服务器性能不均的情况。 
2)、ip_hash 
每个请求按访问ip的hash结果分配，这样每个访客固定访问一个后端服务器，可以解决session的问题。 
3)、fair（第三方） 
按后端服务器的响应时间来分配请求，响应时间短的优先分配。 
4)、url_hash（第三方）

###demo（A机子做负载机子，并实现自身负载）

A机子：192.168.1.101

B机子：192.168.1.102

A机子负载配置：

```
upstream a.com {
	server 127.0.0.1:81 weight=1;
	server 192.168.0.102:81 weight=5;
}
upstream b.com {
	server 127.0.0.1:81 weight=1;
	server 192.168.0.102:81 weight=5;
}
upstream c.com {
    server 127.0.0.1:81 weight=1;
	server 192.168.0.102:81 weight=4;
}
server {
	listen 80;
	server_name a.com b.com;
	location / {
		proxy_pass http://$host;
		proxy_connect_timeout 10s;
	}
}
server {
		include include/ssl.conf;
        server_name c.com;
        location / {
                proxy_pass http://$host;
                proxy_connect_timeout 10s;
        }
}
```

A,B机子站点配置

```
server{ 
    listen 81; 
    server_name a.com; 
    index index.html; 
    root /data0/htdocs/www; 
}
server{ 
    listen 81; 
    server_name b.com; 
    index index.html; 
    root /data0/htdocs/www; 
}
server{ 
    listen 81; 
    server_name c.com; 
    index index.html; 
    root /data0/htdocs/www; 
}

```

**注意：**

1.负载机子上，负载监听的端口应与站点端口不同。

2.确定各个机子的端口通畅





