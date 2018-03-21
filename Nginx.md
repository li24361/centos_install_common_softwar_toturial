## Nginx 安装

yum安装
    
    yum install nginx -y
    
安装完成后，使用 nginx 命令启动 Nginx：
    
    nginx
    
此时，访问 http://<您的域名> 可以看到 Nginx 的测试页面


如果无法访问，请重试用 nginx -s reload 命令重启 Nginx  


## 常用操作

### 反向代理端口到80
打开 Nginx 的默认配置文件 /etc/nginx/nginx.conf 

     /etc/nginx/nginx.conf
     
     
添加以下

<b>proxy_pass http://127.0.0.1:8888;<b>

修改后
        server {
        listen       80 default_server;
        listen       [::]:80 default_server;
        server_name  _;
        root         /usr/share/nginx/html;

        # Load configuration files for the default server block.
        include /etc/nginx/default.d/*.conf;

        location / {
            proxy_pass http://127.0.0.1:8888;
        }

        error_page 404 /404.html;
            location = /40x.html {
        }

        error_page 500 502 503 504 /50x.html;
            location = /50x.html {
        }
    }
    
加载配置

    nginx -s reload
    
### SSL加密

将域名 www.domain.com 的证书文件1_www.domain.com_bundle.crt 、私钥文件2_www.domain.com.key保存到同一个目录，例如/usr/local/nginx/conf目录下。
更新Nginx根目录下 conf/nginx.conf 文件如下：

    server {
        listen 443;
        server_name www.domain.com; #填写绑定证书的域名
        ssl on;
        ssl_certificate 1_www.domain.com_bundle.crt;
        ssl_certificate_key 2_www.domain.com.key;
        ssl_session_timeout 5m;
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2; #按照这个协议配置
        ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:HIGH:!aNULL:!MD5:!RC4:!DHE;#按照这个套件配置
        ssl_prefer_server_ciphers on;
        location / {
            root   html; #站点目录
            index  index.html index.htm;
        }
    }

加载配置

    nginx -s reload
