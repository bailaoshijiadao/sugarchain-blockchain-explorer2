#  sugarchain-blockchain-explorer2

<details>
<summary>Click to view manual deployment</summary>
<br>
Simple blockchain explorer

A web page explorer written in JavaScript and running in the nodejs.

*Note: You only need to set a reachable API address to use it normally, and the block browser does not need to be on the same server as the API node*

### Requires

*  Ubuntu >= 20.04
*  node.js >= 12.14.0

### nvm install
	
	sudo apt-get update
	cd && curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.9/install.sh | bash

	vim /etc/profile

Append at the end of the file

	export NVM_DIR="$HOME/.nvm"
	[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"  # This loads nvm
	[ -s "$NVM_DIR/bash_completion" ] && . "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
	
Then `:wq` save and re source the file

	source /etc/profile

### Nodejs install

	nvm install v12.14.0

### Get the source

    git clone https://github.com/bailaoshijiadao/sugarchain-blockchain-explorer2

### Install node modules

    cd sugarchain-blockchain-explorer2 && npm install

### Configure Port

*Make required changes in sugarchain-blockchain-explorer2/bin/www*

*settings* *port* default 3099

### Configure API adress

*Make required changes in sugarchain-blockchain-explorer2/views/index.ejs*

	var networksConfigs = {
		'SUGAR': {
			'name': 'Main Network (SUGAR)',
			// 'api': 'https://api.sugarchain.org',
			//'api': 'https://api.sugar.wtf',
			'api': 'https://api.sugarchain.net',
			'ticker': 'SUGAR',
			'decimals': 8,
			'hrp': 'sugar'
		},
	}

*make sure to change SugarChain node credentials in `api` can successfully connect*

### Start Explorer

    npm start

### COMPLETE


# Optional Settings

## PM2 settings

PM2 is an excellent Node process management tool that can help applications automatically restart after a crash.

### PM2 install

	npm install pm2 -g

### Start Explorer

Stop the block Explorer first, then use this command to start

	cd sugarchain-blockchain-explorer2
	pm2 start ./bin/www --name sugarchain-blockchain-explorer2

### View project information

	pm2 info sugarchain-blockchain-explorer2

### View resource usage

	pm2 monit
	
## Domain settings

### Point domain to your server

### Install Nginx

	sudo apt-get update
	sudo apt install nginx -y
	
### Create nginx config (replace explorer2.example.com with your domain)

	sudo unlink /etc/nginx/sites-enabled/explorer2.example.com.conf
	rm -rf /etc/nginx/sites-available/explorer2.example.com.conf
	sudo vim /etc/nginx/sites-available/explorer2.example.com.conf
	
Write the following content (replace explorer2.example.com with your domain)
	
	server {
		server_name explorer2.example.com;

		location / {
			proxy_pass http://localhost:3099;
			proxy_http_version 1.1;
			proxy_set_header Upgrade $http_upgrade;
			proxy_set_header Connection 'upgrade';
			proxy_set_header Host $host;
			proxy_cache_bypass $http_upgrade;
		}

		location /socket.io {
			include proxy_params;
			proxy_http_version 1.1;
			proxy_buffering off;
			proxy_set_header Upgrade $http_upgrade;
			proxy_set_header Connection "Upgrade";
			proxy_pass http://127.0.0.1:3099/socket.io;
		}

		listen 80;
	}

### Activate nginx config (replace explorer2.example.com with your domain)

	sudo ln -s /etc/nginx/sites-available/explorer2.example.com.conf /etc/nginx/sites-enabled
	
### Install certbot for ssl certificate

	sudo apt install snapd -y
	sudo snap install --classic certbot
	
### Obtain certificate (replace explorer2.example.com with your domain)

	sudo certbot --nginx -d explorer2.example.com
	
After that blockchain explorer should be accessible via domain you pointed	

</details>

<details>
<summary>点击查看手动部署</summary>
<br>
简单的网页区块链浏览器

一个用JavaScript编写并在nodejs中运行的网页区块链浏览器

*注意: 您只需要设置一个可访问的 API 地址即可正常使用，网页区块浏览器不需要与 API 节点位于同一服务器上*

### 依赖

*  node.js >= 12.14.0

### nvm 安装
	
	sudo apt-get update
	cd && curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.9/install.sh | bash

	vim /etc/profile

英文输入法状态下按下字母i按键, 在文件最后追加以下内容

	export NVM_DIR="$HOME/.nvm"
	[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"  # This loads nvm
	[ -s "$NVM_DIR/bash_completion" ] && . "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
	
然后按下 `Esc` 按键, 输入 `:wq` 保存并重新加载系统环境变量并立即生效

	source /etc/profile

### Nodejs 安装

	nvm install v12.14.0

### 获取源码

    git clone https://github.com/bailaoshijiadao/sugarchain-blockchain-explorer2

### 安装node依赖

    cd sugarchain-blockchain-explorer2 && npm install

### 设置端口

*sugarchain-blockchain-explorer2/bin/www 路径的文件中进行必要的更改*

*修改* *port* 默认端口 3099

### 设置 API 地址

*sugarchain-blockchain-explorer2/views/index.ejs 路径的文件中进行必要的更改*

	var networksConfigs = {
		'SUGAR': {
			'name': 'Main Network (SUGAR)',
			// 'api': 'https://api.sugarchain.org',
			//'api': 'https://api.sugar.wtf',
			'api': 'https://api.sugarchain.net',
			'ticker': 'SUGAR',
			'decimals': 8,
			'hrp': 'sugar'
		},
	}

*确保更改 `api`中的糖链节点凭据可以成功连接*

### 启动区块浏览器

    npm start

### 完成


# 可选的一些设置

## PM2 设置

PM2是一个优秀的节点进程管理工具, 可以帮助应用程序在崩溃后自动重启

### PM2 安装

	npm install pm2 -g

### 使用 PM2 启动区块浏览器

首先应停止前面运行的区块浏览器的运行, 如果没有启动可忽略, 然后再使用下面命令启动即可

	cd sugarchain-blockchain-explorer2
	pm2 start ./bin/www --name sugarchain-blockchain-explorer2

### 查看 PM2 区块浏览器项目信息

	pm2 info sugarchain-blockchain-explorer2

### 查看资源使用情况

	pm2 monit

## 域名设置

### 将域名解析到自己服务器的IP地址

### 安装 Nginx

	sudo apt-get update
	sudo apt install nginx -y
	
### 创建 nginx 配置文件 (将 explorer2.example.com 替换为你的域名)

	sudo unlink /etc/nginx/sites-enabled/explorer2.example.com.conf
	rm -rf /etc/nginx/sites-available/explorer2.example.com.conf
	sudo vim /etc/nginx/sites-available/explorer2.example.com.conf
	
写入以下内容 (将 explorer2.example.com 替换为你的域名)
	
	server {
		server_name explorer2.example.com;

		location / {
			proxy_pass http://localhost:3099;
			proxy_http_version 1.1;
			proxy_set_header Upgrade $http_upgrade;
			proxy_set_header Connection 'upgrade';
			proxy_set_header Host $host;
			proxy_cache_bypass $http_upgrade;
		}

		location /socket.io {
			include proxy_params;
			proxy_http_version 1.1;
			proxy_buffering off;
			proxy_set_header Upgrade $http_upgrade;
			proxy_set_header Connection "Upgrade";
			proxy_pass http://127.0.0.1:3099/socket.io;
		}

		listen 80;
	}

### 激活 nginx 配置 (将 explorer2.example.com 替换为你的域名)

	sudo ln -s /etc/nginx/sites-available/explorer2.example.com.conf /etc/nginx/sites-enabled
	
### 为 ssl 证书安装 certbot

	sudo apt install snapd -y
	sudo snap install --classic certbot
	
### 获得证书 (将 explorer2.example.com 替换为你的域名)

	sudo certbot --nginx -d explorer2.example.com
	
之后, 区块浏览器应该可以通过你指向的域名进行访问

</details>
