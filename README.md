# Ubuntu How To

## stuff I need to do eventually

- [how to add a new user][newUser]
- [how to use chmod][chmod]
- [how to use nano editor][nano]
- [how to use vim editor][vim]
--------------------------------------------
- [how to setup a local host file][local]
- [how to enable certain ports][enablePort]
- [how to set up wordpress][wordpress]
- [how to set up a server with ubuntu][setup]
- [how to install node.js on ubuntu][node]
- [how to install nvm/ or update node][nvm]
- [how to use grep][grep]

[local]:#how-to-setup-a-local-host-file
[enablePort]:#how-to-enable-certain-ports
[wordpress]:#how-to-set-up-wordpress
[grep]:#how-to-use-grep
[nvm]:#how-to-install-nvm-or-update-node
[node]:#how-to-install-node.js-on-ubuntu
[setup]:#how-to-set-up-a-server-with-ubuntu
[home]:#ubuntu-how-to

## how to setup a local host file
this is great for setting creating a websites or at least developing it without
having to buy a domain ... for now . This is essentially working apache for the
most part and then using your personal computer

1. create a conf file for apache
```
sudo cp /etc/apache2/sites-available/000-default.conf  /etc/apache2/sites-available/test.conf
sudo nano /etc/apache2/sites-available/test.conf

// in the test.conf file, add the ServerName test.com and close the file

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /home/jermaine/test
        ServerName test.com
        <Directory /home/jermaine/test/>
            Options Indexes FollowSymLinks
            AllowOverride All
            Require all granted
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        <IfModule mod_dir.c>
            DirectoryIndex index.php index.pl index.cgi index.html index.xhtml index.htm
        </IfModule>

</VirtualHost>

```

2. next enable the site

```
sudo a2ensite test.conf

sudo service apache2 reload
```

3. now, go to your personal and run notepad as an administrator

4. once in notepad, open a file to the path `C:\Windows\System32\drivers\etc\hosts`

5. now in the hosts file insert your vps ip address and the ServerName

```
111.111.111.111 test.com
```

6. and that is about it.

[go back home][home]

## how to enable certain ports
This is pretty easy you just type in one command

```
 sudo ufw allow enterPortNumber
```
**reference**
[firewall](https://help.ubuntu.com/lts/serverguide/firewall.html)

[go back home][home]

## how to set up wordpress

1. log into mysql and type this into the terminal

```mysql
	CREATE DATABASE wordpress DEFAULT CHARACTER SET utf8 COLLATE utf8_unicode_ci;
```
2. create a user specifically for wordpress and type

```mysql
	GRANT ALL ON wordpress.* TO 'wordpressuser'@'localhost' IDENTIFIED BY 'password';
	FLUSH PRIVILEGES;
	EXIT;
```
3. install the additional php extensions

```
	sudo apt-get update
	sudo apt-get install php-curl php-gd php-mbstring php-mcrypt php-xml php-xmlrpc
	sudo systemctl restart apache2
```
4. go into apache2.conf file to allow htaccess overrides

```
	sudo nano /etc/apache2/apache2.conf

	// add this into the file

	<Directory /var/www/html/>
    	AllowOverride All
	</Directory>
```
5. enable the changes and restart apache2

```
	sudo a2enmod rewrite
	sudo apache2ctl configtest
	sudo systemctl restart apache2
```
6. download wordpress and unzip it

```
	cd /tmp
	curl -O https://wordpress.org/latest.tar.gz
	tar xzvf latest.tar.gz
```
7.  do some shit with wordpress

```
	touch /tmp/wordpress/.htaccess
	chmod 660 /tmp/wordpress/.htaccess
	cp /tmp/wordpress/wp-config-sample.php /tmp/wordpress/wp-config.php
	mkdir /tmp/wordpress/wp-content/upgrade
	sudo cp -a /tmp/wordpress/. /var/www/html
```
8. configure wordpress

```
	sudo chown -R yourName:www-data /var/www/html
	sudo find /var/www/html -type d -exec chmod g+s {} \;
	sudo chmod g+w /var/www/html/wp-content
	sudo chmod -R g+w /var/www/html/wp-content/themes
	sudo chmod -R g+w /var/www/html/wp-content/plugins
```

9. creating keys and passwords
```
	// copy the printed keys
	curl -s https://api.wordpress.org/secret-key/1.1/salt/

	sudo nano /var/www/html/wp-config.php

	// place the printed keys in the file
	// and add in the database information  like this

	define('DB_NAME', 'wordpress');

	/** MySQL database username */
	define('DB_USER', 'wordpressuser');

	/** MySQL database password */
	define('DB_PASSWORD', 'password');

	. . .

	define('FS_METHOD', 'direct');
```
10. Setup the apache server to host the wordpress, and then you are done

[go back home][home]

## how to use grep
- Alright so the grep keyword searches through any file  that contains the string
or words that you are looking for.
- **grep does not** : search a folder it only searches what a specific file, or
the files that are in the current directory/folder

```
	 grep "some word" /path/to/file
```
### search all files in each directory

```
	grep -r  "some word" /path/to/file

	//Note: it will search every file and every file in each folder
```

### how to print out all the files that contain the search word

```
	grep -l "some word" /path/to/file

```

### grep ignoring word casing

```
	grep -i "some word" /path/to/file

	// Note: so it will search for the word whether it be uppercase, lowercase, ect..
```

### searching the exact word

```
	grep -w "some word" /path/to/file
```

### search for two different words

```
	egrep "word1|word2" /path/to/file

	// Note: you can only search two different phrases or words, not three of more
```

### count a number of times the word has come up

```
	grep -c "some word" /path/to/file
```

### show the line number where word has been matched

```
	grep -n "some word" /path/to/file
```

### ignore the search word, but print out the rest of content of the file

```
	grep -v "some word" /path/to/file
```

[go back home][home]

## how to install nvm/ or update node
- Either do one or the other
- [here is the repository](https://github.com/creationix/nvm)

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

[go back home][home]


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

### OR
1. install node version manager

```
	sudo apt-get update
	wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash
	exit



```
2. log back in and install node

```
	nvm -v
	nvm install node
```

[go back home][home]


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
	sudo chmod 700 ~/.ssh
	sudo nano ~/.ssh/authorized_keys
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
	sudo chmod 600 ~/.ssh/authorized_keys

	// might have to possibly enter this as well
		sudo chown jermaine -R ~/.ssh


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

	// might have to possibly enter this as well
		sudo service sshd restart
```

10. set up basic firewall
```
	sudo ufw allow OpenSSH

	sudo ufw enable

	sudo ufw status

```
11. and I think that is it

[go back home][home]
