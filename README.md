#  sugarchain-blockchain-explorer2

================

Simple blockchain explorer

An open source block explorer written in node.js.

### Requires

*  node.js >= 8.17.0 (12.14.0 is advised for updated dependencies)

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


