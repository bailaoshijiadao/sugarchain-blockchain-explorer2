#  sugarchain-blockchain-explorer2

<details>
<summary>Click to view manual deployment</summary>
<br>
Simple blockchain explorer

A web page explorer written in JavaScript and running in the nodejs.

*Note: You only need to set a reachable API address to use it normally, and the block browser does not need to be on the same server as the API node*

### Requires

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

在文件最后追加以下内容

	export NVM_DIR="$HOME/.nvm"
	[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"  # This loads nvm
	[ -s "$NVM_DIR/bash_completion" ] && . "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
	
然后 `：wq` 保存并重新加载系统环境变量并立即生效

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

首先停止块资源管理器，然后使用此命令启动

	cd sugarchain-blockchain-explorer2
	pm2 start ./bin/www --name sugarchain-blockchain-explorer2

### 查看 PM2 区块浏览器项目信息

	pm2 info sugarchain-blockchain-explorer2

### 查看资源使用情况

	pm2 monit

</details>
