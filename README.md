# Linux How To

## phpmyadmin
- [how to change the url][change-url]
- [enable authentication page][php-auth-page]

## editors
- [how to use nano editor][nano]
- [how to use vim editor][vim]

## chgrp, chown, chmod

- [how to use chgrp][chgrp]
- [how to use chown][chown]
- [how to use chmod][chmod]
- [how to create a group][group]

## custom commands
- [how to use alias][alias]
- [create commands permanently][permanent-command]
- [how to use bash functions][bash-functions]

## ufw
- [how to add a port number][allow-port]
- [how to show the list of rules][list-ports]
- [how to deny a rule/port][deny-port]
- [how to delete a rule/port][delete-port]


## user
- [how to switch to a different user][switchUser]
- [how to add a new user][newUser]
- [how to list local users][local-user]
- [how to delete a user][delete-user]
- [how to change a username][change-user]
- [how to change a password][change-passwd]

## common commands
- [how to use grep][grep]
- [how to use find][find]

## installation
- [how to install node.js on ubuntu][node]
- [how to install nvm/ or update node][nvm]
- [how to set up wordpress][wordpress]
- [how to setup laravel][laravel]
- [how to install phpmyadmin][phpmyadmin]


## let's encrypt
- [how to create an let's encrypt][ssl]
- [how to https a domain][https-domain]
- [how to update certbot][update-certbot]

## other
- [how to setup a local host file][local]
- [how to enable certain ports][enablePort]
- [how to set up a server with ubuntu][setup]
- [how to change the timezone][set-time]

## root
- [how to look into a directory without having a permission][root-permission]


## errors
- [Client with the currently selected authenticator does not support any combination of challenges that will satisfy the CA.][ssl-error]

## other 
- cat
- head 
- tail 
- less
- tar 
- sed 
- awk 
- sort



----
[change-url]:#how-to-change-the-url
[set-time]:#how-to-change-the-timezone
[delete-port]:#how-to-delete-a-port
[allow-port]:#how-to-add-a-port-number
[root-permission]:#how-to-look-into-a-directory-without-having-a-permission
[update-certbot]:#how-to-update-certbot
[https-domain]:#how-to-https-a-domain
[bash-functions]:#how-to-create-bash-functions
[permanent-command]:#create-commands-permanently
[alias]:#how-to-use-alias
[phpmyadmin]:#how-to-install-phpmyadmin
[vim]:#how-to-use-vim-editor
[nano]:#how-to-use-nano-editor
[ssl-error]:#how-to-authenticate-a-domain-with-ssl
[change-passwd]:#how-to-change-a-password
[change-user]:#how-to-change-a-username
[delete-user]:#-how-to-delete-a-user
[chgrp]:#how-to-use-chgrp
[group]:#how-to-create-a-group
[local-user]:#how-to-list-local-users
[chown]:#how-to-use-chown
[switchUser]:#how-to-switch-to-a-different-user
[newUser]:#how-to-add-a-new-user
[ssl]:#how-to-create-an-ssl-certificate
[chmod]:#how-to-use-chmod
[find]:#how-to-use-find
[laravel]:#how-to-setup-laravel
[local]:#how-to-setup-a-local-host-file
[enablePort]:#how-to-enable-certain-ports
[wordpress]:#how-to-set-up-wordpress
[grep]:#how-to-use-grep
[nvm]:#how-to-install-nvm-or-update-node
[node]:#how-to-install-nodejs-on-ubuntu
[setup]:#how-to-set-up-a-server-with-ubuntu
[home]:#linux-how-to
[list-ports]:#how-to-show-the-list-of-rules
[deny-port]:#how-to-deny-a-port
[php-auth-page]:#enable-authentication-page


### enable authentication page

<details>
<summary>
View Content
</summary>

**reference**
- [How To Install and Secure phpMyAdmin on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-16-04)


1. create an .htaccess file and add this
```
sudo vim  /usr/share/phpmyadmin/.htaccess

...
AuthType Basic
AuthName "Restricted Files"
AuthUserFile /etc/phpmyadmin/.htpasswd
Require valid-user
```

2. now create the .htpasswd for the .htaccess

```
sudo htpasswd -c /etc/phpmyadmin/.htpasswd insertUsername

// after that it will ask you for a password
```

3. now restart it

```
sudo service apache2 restart
```

</details>

[go back :house:][home]


### how to change the url

<details>
<summary>
View Content
</summary>

**reference**
- [How to Change and Secure Default PhpMyAdmin Login URL](https://www.tecmint.com/change-secure-phpmyadmin-login-url-page/)

1. vim inside apache.conf
```
sudo vim /etc/phpmyadmin/apache.conf
```

2. in the file change the alias which originally has `/phpmyadmin`

```
# Alias /phpmyadmin /usr/share/phpmyadmin
Alias /mynewadmin /usr/share/phpmyadmin
```

3. now reload apache2

```
sudo service apache2 reload
```

</details>

[go back :house:][home]

### how to change the timezone

<details>
<summary>
View Content
</summary>

**reference**
- [set timezone](https://www.tecmint.com/set-time-timezone-and-synchronize-time-using-timedatectl-command/)

1. first list the available timezones
```
timedatectl list-timezones
```

2. find the one you want to use and set it

```
timedatectl set-timezone "America/New_York"

```

3. if you want to change it back to UTC do this

```
timedatectl set-timezone UTC
```

</details>

[go back :house:][home]

### how to delete a port

<details>
<summary>
View Content
</summary>

**reference**
- [UFW](https://help.ubuntu.com/community/UFW)

```
sudo ufw status numbered

sudo ufw delete 4
```

</details>

[go back :house:][home]


### how to deny a port

<details>
<summary>
View Content
</summary>

**reference**
- [UFW](https://help.ubuntu.com/community/UFW)

```
sudo ufw status numbered

sudo ufw deny 4
```

</details>

[go back :house:][home]

### how to show the list of rules

<details>
<summary>
View Content
</summary>

**reference**
- [UFW](https://help.ubuntu.com/community/UFW)

```
sudo ufw status numbered
```

</details>

[go back :house:][home]



### how to add a port number

<details>
<summary>
View Content
</summary>

**reference**
- [UFW](https://help.ubuntu.com/community/UFW)

```
sudo ufw allow 1337
```

</details>

[go back :house:][home]


### how to look into a directory without having a permission

<details>
<summary>
View content
</summary>


**reference**
- [cd into directory without having permission](https://stackoverflow.com/questions/8221820/cd-into-directory-without-having-permission)

```
sudo su

// This command give you root privilege so now you don't have to worry about
// any permissions blocking you
```

</details>

[go back :house:][home]


### how to update certbot
<details>
<summary>
View Content
</summary>

**reference**
- [certbot](https://certbot.eff.org/lets-encrypt/ubuntuxenial-apache)

#### 1st option

```
 sudo apt-get update
 sudo apt-get install software-properties-common
 sudo add-apt-repository universe
 sudo add-apt-repository ppa:certbot/certbot
 sudo apt-get update
 sudo apt-get install certbot python-certbot-apache

```


#### 2nd option

```
sudo add-apt-repository ppa:certbot/certbot
sudo apt-get update
sudo apt-get install certbot
```
</details>

[go back :house:][home]


### how to https a domain

<details>
<summary>
View Content
</summary>

```
sudo certbot --apache -d <insert domain>
```
</details>

[go back :house:][home]


### how to create bash functions

<details>
<summary>
View content
</summary>

**reference**
- [Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/bash-functions.php)


here is what worked for me so far

1. create a bin file and it into the bashrc if you haven't done it already

```

mkdir ~/bin

// open up bash


sudo nano ~/.bashrc

// now insert the code

export PATH=$PATH:~/bin

```

2. now create an sh file creating a function

```
nano ~/bin/hello.sh


//inside hello.sh

print_hello(){


echo "hello world";

}


```


3. make all the files executable

```
chmod -R +x ~/bin;
```

4. now you can run the file

```
hello.sh
```

</details>

[go back :house:][home]

### create commands permanently

<details>
<summary>
View content
</summary>

**reference**
- [An Introduction to Useful Bash Aliases and Functions](https://www.digitalocean.com/community/tutorials/an-introduction-to-useful-bash-aliases-and-functions)
- [How can I create a custom terminal command (to run a script)?](https://askubuntu.com/questions/118312/how-can-i-create-a-custom-terminal-command-to-run-a-script)

1. open up the `bashrc` file and put your alias command inside of it

```
sudo nano ~/.bashrc

//inside the bashrc file add your command anywhere

alias .2="cd ../../"
```

#### other option

1. create a file with some command you want

```
// create the file

nano sites

// inside sites add your specific command like this
// Note: its important to add a semi-colon at the end

cd /etc/apache2/sites-available;

```

2. now create a bin folder and move the file into the bin

```
// make the bin

mkdir ~/bin

// move the file in the bin

mv sites ~/bin/sites

```

3. make the files executable

```
sudo chmod -R +x ~/bin

```

4. now open up the bashrc file and  add this code

```
// open up bash


sudo nano ~/.bashrc

// now insert the code

export PATH=$PATH:~/bin
```

5. so this should make the `sites` command work

</details>

[go back :house:][home]


### how to use alias

<details>
<summary>
View content
</summary>

**reference**
- [An Introduction to Useful Bash Aliases and Functions](https://www.digitalocean.com/community/tutorials/an-introduction-to-useful-bash-aliases-and-functions)

Declaring aliases in bash is very straight forward. It's so easy that you should try it now.
The alias keyword will make it alot easier to create custom commands
`alias alias_name="command_to_run"`


```
// this should go back 2 folders when you type in ..2

alias ..2="cd ../../"
```


#### if want to remove an alias

```
unalias ..2;
```


</details>

[go back :house:][home]



### how to install phpmyadmin

<details>
<summary>
View content
</summary>

**reference**
- [Install phpMyAdmin on Ubuntu 16.04](https://www.rosehosting.com/blog/install-phpmyadmin-on-ubuntu-16-04/)
- [How to solve the phpmyadmin not found issue after upgrading php and apache?](https://askubuntu.com/questions/387062/how-to-solve-the-phpmyadmin-not-found-issue-after-upgrading-php-and-apache)

1. update linux

```
sudo apt-get update && apt-get upgrade
```

2. install phpmyadmin

```
sudo apt-get install phpmyadmin
```

3. When prompted for a web server choose **Apache2**



4. In the next prompt click **yes** to configure a database for phpmyadmin



5. Next, set the password and confirm the password you created to get into phpmyadmin


6. Now add this in the terminal, I'm assuming that you are creating a link connection and then turning on phpmyadmin

```
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf;
sudo a2enconf phpmyadmin.conf;
sudo service apache2 reload
```


7. Now you should be able to go to your site at  `http://yourIPaddress/phpmyadmin`


#### How to change the PHPMyAdmin path name


1. Open up the conf file

```
sudo nano /etc/apache2/conf-available/phpmyadmin.conf

```

2. On line 3, change the path name

```
Alias /newPathName /usr/share/phpmyadmin
```



</details>

[go back :house:][home]


### how to use vim editor

<details>
<summary>View content</summary>

**reference**
-[vim keyboard shortcuts](https://www.maketecheasier.com/vim-keyboard-shortcuts-cheatsheet/)
- [Cut/copy and paste using visual selection](http://vim.wikia.com/wiki/Cut/copy_and_paste_using_visual_selection)

Command|Explanation
-|-
esc|Gets out of the current mode into the “command mode”. All keys are bound of commands.
:|“Last-line mode” where Vim expects you to enter a command such as to save the document.
$|jumps to the end of line
0|jumps to the beginning of line
dd|deletes a line.
G|jumps to the end of the file
gg|jumps to the beginning of the file
i|“Insert mode” for inserting text. Keys behave as expected.
o|Begin a new line below the cursor
p|paste content
u|undo the last operation.
v|Allows you to select multiple text
d|deletes a character OR cuts selected text
y| copies selected content
?| finds a word in the file, and pressing **n** goes to the next word


#### Cut, Paste, Select
Command|Explanation
-|-
v or V | Selects multiple text
y | copies selected content
yy | copies current line
p | paste content after cursor line
P | paste content before cursor line
V then d then p | To select text, the cut text, then paste text


#### Navigate Document
Command|Explanation
-|-
G| jumps to the end of the file
gg| jumps to the beginning of the file
</details>


[go back :house:][home]

### how to use nano editor

<details>
<summary>View content
</summary>

**reference**
- [useful keyboard commands](https://staffwww.fullcoll.edu/sedwards/Nano/UsefulNanoKeyCommands.html)
- [Copy (only copy, not cutting) in Nano?](https://askubuntu.com/questions/833102/copy-only-copy-not-cutting-in-nano)

Command | Explanation
-|-
alt + \ | jumps to beginning of file
alt + / | jumps to end of file
ctr + 6 | allows you to select multiple lines if you move up or down
alt + 6 |  copies higlighted text
ctr + a | jumps to end of line
ctr + e | jumps to beginning of line
ctr + d | delete content
alt + r | search and replace
ctr + k | cut  content
ctr + u | paste content

</details>



[go back :house:][home]

### how to authenticate a domain with ssl

**reference**
- [lets encrypt](https://community.letsencrypt.org/t/solution-client-with-the-currently-selected-authenticator-does-not-support-any-combination-of-challenges-that-will-satisfy-the-ca/49983)
- [Solution: Client with the currently selected authenticator does not support any combination of challenges that will satisfy the CA](https://community.letsencrypt.org/t/solution-client-with-the-currently-selected-authenticator-does-not-support-any-combination-of-challenges-that-will-satisfy-the-ca/49983)
- [How to stop using TLS-SNI-01 with Certbot](https://community.letsencrypt.org/t/how-to-stop-using-tls-sni-01-with-certbot/83210)

**If you’re serving files for that domain out of a directory on that server**
```
sudo certbot --authenticator webroot --webroot-path <path to served directory> --installer apache -d <domain>
```

**If you’re not serving files out of a directory on the server**
```
sudo certbot --authenticator standalone --installer apache -d <domain> --pre-hook "service apache stop" --post-hook "service apache start"
```

[go back home][home]

### how to change a password

```
sudo passwd username
```

[go back home][home]

### how to change a username

```
usermod -l new_username old_username
```

[go back home][home]

### how to delete a user

1. in the terminal
```
sudo userdel username
```
2. delete home directory of the user

```
sudo rm -r /home/username
```

[go back home][home]

### how to use chgrp

**reference**
- [CHGRP COMMAND EXPLAINED IN LINUX WITH EXAMPLES](https://www.linuxnix.com/chgrp-command-explained-linux-examples/)

```
chgrp <new group> <insert path to file>

// changes the group name of a file or folder
```
```
chgrp -R <new group> <insert path to file>

// changes the group name of a file or folder recursively
```
```
chgrp -f <new group> <insert path to file>

// changes the group name of a file or folder forcefully
```

[go back home][home]

### how to create a group

**reference**
- [Howto: Linux Add User To Group](https://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)
- [Linux: Show All Members of a Group](https://www.cyberciti.biz/faq/linux-list-all-members-of-a-group/)


### how to show all members of a group
```
grep -i --color 'insert group name' /etc/group
```
**OR**

```
sudo apt install members

members webmaster
```

### how to create a user and add it to a group
```
useradd -g insertGroup insertUser
```

### how to add existing user to a group
```
usermod -aG insertGroup insertUser
```

[go back home][home]

## how to list local users

**reference**
- [A command to list all users? And how to add, delete, modify users?](https://askubuntu.com/questions/410244/a-command-to-list-all-users-and-how-to-add-delete-modify-users)

this command sort of works. But, it lists a lot of other commands and the local
users at the bottom

```
cut -d: -f1 /etc/passwd
```

[go back home][home]

## how to use chown

**reference**
- [chown examples](http://www.thegeekstuff.com/2012/06/chown-examples)


### how change the owner to a folder
```
chown jermaine <insert folder name>
```
### how change the group to a folder
```
chown :developer <insert folder name>
```
### how change the group and owner to a folder
```
chown jermaine:developer <insert folder name>

// how to do this recursively

chown -R jermaine:developer <insert folder name>
```
### how change the owner/group if owned by a different entity
```
chown  --from=chris jermaine <insert folder name>

chown  --from=:production :development <insert folder name>
```
### copy the owner/group settings from one file to another
```
// this copies the owner and group settings from the file "file"
// and apply it to the file "tmpfile"

chown --reference=file tmpfile
```

[go back home][home]



## how to switch to a different user

```
su - <insert name>
```
[go back home][home]

## how to add a new user

```
sudo adduser <insert name>
```
[go back home][home]

## how to create an ssl certificate

**reference**
- [How To Secure Apache with Let's Encrypt on Ubuntu 14.04](https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-14-04)

### how to use "Let's Encrypt" to perform SSL certification

1. download Let's Encrypt

```
sudo add-apt-repository ppa:certbot/certbot

sudo apt-get update

sudo apt-get install python-certbot-apache
```

2. set up the SSL certificate

```
sudo certbot --apache -d example.com

// if you want to certify multiple domains
sudo certbot --apache -d example.com -d www.example.com
```

3. setup auto renewal

```
sudo crontab -e

// in the text editor add this
15 3 * * * /usr/bin/certbot renew --quiet

// At 3:15am the certbot will check if the certificates need to be renewed
```

[go back home][home]

## how to use chmod

**reference**
- [chmod](https://en.wikipedia.org/wiki/Chmod)
- [7 chmod command examples for beginners](http://www.thegeekstuff.com/2010/06/chmod-command-examples/)

### numerical permissions

#|Permission|rwx
-|-|-
7|read,write, and execute|rwx
6|read and write|rw-
5|read and execute|r-x
4|read only|r--
3|write and execute|-wx
2|write only|-w-
1|execute only|--x
0|none|---

### reference table

Reference|Class|Description
-|-|-
u|owner|file's owner
g|group|users who are members of the file's group
o|others|users who are neither the file's owner nor members of the file's group
a|all|all three of the above, same as ugo

### operator table

Operator|Description
-|-
+|adds the specified modes to the specified classes
-|removes the specified modes from the specified classes
=|the modes specified are to be made the exact modes for the specified classes

### mode table

Mode|Name|Description
-|-|-
r|read|read a file or list a directory's contents
w|write|write to a file or directory
x|execute|execute a file or recurse a directory tree
X|special execute|which is not a permission in itself but rather can be used instead of x. It applies execute permissions to directories regardless of their current permissions and applies execute permissions to a file which already has at least one execute permission bit already set (either owner, group or other). It is only really useful when used with '+' and usually in combination with the -R option for giving group or other access to a big directory tree without setting execute permission on normal files (such as text files), which would normally happen if you just used "chmod -R a+rx .", whereas with 'X' you can do "chmod -R a+rX ." instead
s|setuid/gid| allows a person to execute a program with the user and groups permmision according to [this](http://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) source
t|sticky| prevents a file or directory to be renamed or removed [examples](http://www.miniaturelinux.com/Linux-Access-Modes-and-Sticky-Bits-Examples.php)

### FAQ

#### What does execute do?
So there are certain words that if you type in the terminal will
execute a function. Essentially they are commands, so if you remove the permission
of execute it will not a script that can run a command. Here is a little trick
I learned, if you create a file like `touch run`. This will will create a
file called run, next you should open the file and insert ` ls -la`. Save the
file and insert the file the terminal to execute the command ` ./run`
this should run the ls -la command. If you remove the execute permission it
will not work... at least I think


#### What does the mode 's' do?

**reference**
- [LinuxG](http://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/)
- [how does the sticky bit work?](https://unix.stackexchange.com/questions/79395/how-does-the-sticky-bit-work)

the **setuid** and **setgid** gives permission for the user and the group to execute
a file so when you do a command `chmod o+s ./script` you are giving the permission  
for anyone/others to execute the file called script. Not only that, **it will execute
the program as if you are the user or group**





### examples
```
-rwxr-xr-x 14 jermaine jermaine 4.0K Sep  4 18:00 filename.txt

// gives permission to read and write to the owner and group
chmod 660 filename.txt
-rw-rw---- filename.txt


// owner: read,write, and execute
// group: read,write, and execute
// others: read and write
chmod 776 filename.txt
-rwxrwxrw- filename.txt



// owner: write
// group: write
// others: write
chmod a+w filename.txt
--w--w--w- filename.txt

//-rw--w--w- filename.txt
chmod u=o filename.txt
//-rw--w-rw- filename.txt


```


[go back home ][home]

## how to use find
the find command tries to find a specific file that is in a specific location

**reference**
- [25 ways to use the find command](http://www.binarytides.com/linux-find-command-examples/)



**finds name of file in specific path**
```
find ./images -name "dog.jpg"
// prints out the path to dog.jpg, for example

./images/animals/dog.jpg


// AND, you can find files by their extension name

find ./images -name "*.jpg"

.images/animals/dog.jpg
.images/furniture/chair.jpg
.images/entertainment/nudes.jpg

```
**finds name of files and ignores the casing**
```
find ./music -iname 'BLUe*'

./music/I am having a blue day.mp3
./music/Blueberry dreams.mp3
./music/sad and blue.mp3
```
**limits the depth of directory traversal**
```
find ./img  -maxdepth 2 -iname "*.png"
./img/eat.png
./img/alphabet/a.png
./img/anatomy/dick.png

find ./img  -maxdepth 3 -iname "*.png"

./img/eat.png
./img/alphabet/a.png
./img/anatomy/dick.png
./img/anatomy/bones/femur.png
./img/alphabet/chinese/chingchong.png


```
[go back home][home]

**excludes the name or file extension**
```
find ./public
style.css
image.jpg
base.js

find ./public ! -name "*.js"
style.css
image.jpg

```
**combine multiple queries**
```
find ./images -name "*.gif"
./images/find.gif
./images/the.gif

find ./images -name "*.gif" ! -name "*e"
./images/find.gif

// Note: the query results will only print out the files that match all the queries
```

**OR**
```
find -name '*.php' -o -name '*.txt'
./abc.txt
./subdir/how.php
./abc.php
./cool.php

// Note: the query results will print out anything that matches the multiple queries
```
[go back home][home]

**Search only files or only directories**
```
find ./test -name abc*
./test/abc.txt
./test/abc

Only files

find ./test -type f -name "abc*"
./test/abc.txt

Only directories

find ./test -type d -name "abc*"
./test/abc
```

**Find files belonging to particular user**
```
find . -user bob
.
./abc.txt
./abc
./subdir
./subdir/how.php
./abc.php
```
**Search files belonging to group**
```
find /var/www -group developer
```
**Find files accessed in last N days**
```
find / -atime 50
// shows the days which is 50
```


[go back home][home]

**Find files belonging to particular user**
```
 find . -user root
.
./abc.txt
./abc
./subdir
./subdir/how.php
./abc.php
```

**Find files in a size range**
```
find / -size +50M -size -100M

// Different file sizes
 G - gigabytes
 M - megabytes
 k - kilobytes
 b - bytes
```

**Find files with certain permissions**
```
find . -type f -perm 0664
./abc.txt
./subdir/how.php
./abc.php
./cool.php

```

[go back home][home]

## how to setup laravel
```
sudo apt-get update upgrade

sudo apt-get install git zip

sudo apt-get install curl php-curl php-mcrypt php-mbstring php-gettext

sudo phpenmod mcrypt; sudo phpenmod mbstring; sudo a2enmod rewrite

sudo service apache2 restart

curl -sS https://getcomposer.org/installer | php

sudo mv composer.phar /usr/local/bin/composer

composer create-project laravel/laravel your-project --prefer-dist

sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/laravel.conf

sudo nano laravel.conf

// inside laravel.conf
<VirtualHost *:80>
        ServerName work.com
        DocumentRoot /var/www/html/your-project/public

        <Directory /var/www/html/your-project/public>
            AllowOverride All
            Require all granted
        </Directory>
</VirtualHost>

sudo a2ensite laravel.conf; sudo service apache2 reload

cd your-project

sudo chmod -R 755 ./; sudo chmod -R o+w ./storage

```
**reference**
- [Install laravel 5 on Ubuntu 16.04](https://askubuntu.com/questions/764782/install-laravel-5-on-ubuntu-16-04)
- [Installing Laravel PHP Framework on Ubuntu](https://www.howtoforge.com/tutorial/install-laravel-on-ubuntu-for-apache/)

[go back home][home]

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
