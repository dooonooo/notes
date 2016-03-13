title: Rsync部署HEXO，使用HTTPS，附加HTTP2
date: 2015-11-14 10:36:54
tags:
- https
- http2
- hexo
- rsync

---

首先如果想部署在GITHUB上使用HTTPS，就目前来看那是不可能，除非使用github.io域名，所以首先要有一个VPS或云主机，之前做SS时，在digitalocean买了一个水滴，使用也不算多我的BLOG访问量也不高，为了省钱就一起搞吧，也是为了充分利用资源吧  O(∩_∩)O

我的digitalocean推荐链接：使用我的链接，你将有10美元奖励，我也有额外获得。 <!--more--> 
<https://www.digitalocean.com/?refcode=7c320d50fe04>

### 下载nginx

	cd ~/tmp/
	wget http://nginx.org/download/nginx-1.9.6.tar.gz
	wget https://www.openssl.org/source/openssl-1.0.2d.tar.gz
	
	tar -xzf nginx-1.9.6.tar.gz
	tar -xzf openssl-1.0.2d.tar.gz

### 编译安装

	cd nginx-1.9.6
	./configure --with-openssl=/home/dong/tmp/openssl-1.0.2d/ --with-http_spdy_module --with-http_ssl_module
	make
	sudo make install
	
使用 `--with-openssl`指定openssl文件位置

### 编辑nginx配置文件

 `vi /usr/local/nginx/conf/nginx.conf`

	# HTTPS server 	
	server {
    #   此处添加HTTP2 即可启用HTTP2
        listen       443 ssl http2;
        server_name  localhost;
        # 证书文件路径
        # 证书私钥文件路径
        ssl_certificate      ./ssl/cert.pem;
        ssl_certificate_key  ./ssl/cert.key;

    #   ssl_session_cache    shared:SSL:1m;
        ssl_session_timeout  5m;

    #    ssl_ciphers  HIGH:!aNULL:!MD5;
    #    ssl_prefer_server_ciphers  on;
    #    location / {
    # 在root后面位网站的根目录
            root   /home/wwwroot/blog/; 
            index  index.html index.htm;
        }
     # }
        
编译安装的直接去掉配置文件中相应条目的注释就好了，如果是使用yum或apt-get自动安装的，可能需要手工添加
	
### 重载nginx
	
	/usr/local/nginx/sbin/nginx -t
	/usr/local/nginx/sbin/nginx -s reload

  使用 `-t`参数检查配置文件的正确性，避免配置文件出错nginx停止

不仅使用了HTTPS，还是使用HTTP2。瞎折腾 -_-|||

### rsync部署hexo
我选择的是rsync模式，服务器上需要安装有rsync，一般linux中都安装了rsync，命令`rsync --version`确定是否安装，若没有安装，`yum install rsync`或 `apt-get install rsync`安装就好啦。

安装hexo-deployer-rsync
npm install hexo-deployer-rsync --save

#### 修改配置

修改hexo的主配置文件`_config.yml`

	deploy:
	- type: rsync
	  host: 主机地址(填你主机的ip)
	  user: lidong（主机登陆用户名）
	  root: /home/wwwroot/blog/
	  port: 22
	  delete: true
	  verbose: true
	  ignore_errors: [true|false] 
	- type: git
	   repo: git@github.com:dongoo/dongoo.github.io.git
	   branch: 
	   message: 
	  
多个部署，之前使用git部署，现在保留，使用git方便版本管理。也以防哪天挂了，可以再搞起。
  相关内容参看官方文档: <https://hexo.io/zh-cn/docs/deployment.html>
 
 <strong>你会发现选择使用rsync部署时，没有填写密码选项，不用认证吗？那是不可能的！不使用密码就要用密钥，和部署github时生成密钥相似</strong>。
 而且这对密钥是可以通用的哟，你只是公开的你的公钥，私钥自己保留着，破解？目前那是相当困难滴。
 我之前多次尝试部署不成功，都是没有意识到这一点。所以都失败了。
 
 PS:在digitalocean中可以在创建水滴(Droplet)时候，可以直接添加SSHkey，
digitalocean自动将SSHkey写入到系统中，若你使用的是其他主机，请检索相关资料啦。
总之，<strong>你需要能在本机使用SSHkey而不是密码，登陆到服务器</strong>，才能成功通过rsync部署HEXO。

当一切都OK时，是 `hexo deploy` 一下，看看效果。
别忘记了修改DNS解析。自己实验的时候可以先修改hosts实现快速切换。




