# Ubuntu How To
---------------------------
---------------------------
- [how to set up a server with ubuntu][setup]
- [how to install node.js on ubuntu][node]
- [how to install nvm/ or update node][nvm]

[nvm]:#how-to-install-nvm-or-update-node
[node]:#how-to-install-node.js-on-ubuntu
[setup]:#how-to-set-up-a-server-with-ubuntu
[home]:#ubuntu-how-to

## how to install nvm/ or update node
- Either do one or the other
```
	curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash
```
### OR
```
	wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash
```
- then close the terminal and go back into it again. And check to see if it is working
```
	exit

	// once you go back into the terminal

	nvm -v
```
the nvm should change node and npm to the most recent version.


## how to install node.js on ubuntu
1. install node and npm with apt-get
```
	sudo apt-get update
	sudo apt-get install nodejs
	sudo apt install nodejs-legacy
	sudo apt-get install npm
```

2. install node with PPA(personal package archive)
```
	cd ~
	curl -sL https://deb.nodesource.com/setup_<insert node.js version> -o nodesource_setup.sh

	// you can check the contents of the setup like this
	nano nodesource_setup.sh
```
- then run the setup
```
	sudo bash nodesource_setup.sh
```
- next add this shit
```
	sudo apt-get install nodejs
	sudo apt-get install build-essential
```

##  how to set up a server with ubuntu
1. ssh into your server
```
	ssh root@your_server_ip
```
2. add a new user
```
	adduser jermaine
```
3. give root privileges to your new user
```
	usermod -aG sudo jermaine
```
4. switch to the user account
```
	su - jermaine
```
5. Create an ssh directory and authorized_keys file in the user account
```
	mkdir ~/.ssh
	chmod 700 ~/.ssh
	nano ~/.ssh/authorized_keys
```
6. add the public key by using cat command to display it
```
	//Personal Computer
	cat ~/.ssh/id_rsa.pub

	ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAA...


	// Inside authorized_keys file

	ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAA...

```
7. restrict the permissions of the authorized_keys, and exit out of user account
```
	chmod 600 ~/.ssh/authorized_keys

	exit
```

8. open up ssh configuration
```
	sudo nano /etc/ssh/sshd_config
```
9. make sure all these options have these values, then reload
```
	PasswordAuthentication no
	PubkeyAuthentication yes
	ChallengeResponseAuthentication no

	sudo systemctl reload sshd
```

10. set up basic firewall
```
	sudo ufw allow OpenSSH

	sudo ufw enable

	sudo ufw status

```
11. and I think that is it

[go back home][home]
