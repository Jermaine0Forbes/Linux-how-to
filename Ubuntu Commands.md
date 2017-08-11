# Linux/Ubuntu Commands
---------------------------
---------------------------


### sudo
- The SuperUserDo is the most important command Linux newbies will use.
Every single command that needs root's permission, needs this command

### apt-get
	-to install, remove and upgrade any package we've Advanced Packaging Tool (APT) package manager.
	The apt-get command will help you installing the software you need to run in your Linux.

### adduser <insert name>
	-add a user or group to the system

### gpasswd -a <insert user name> sudo

### su <insert user name>
	-change user ID or become superuser

### exit
	-cause normal process termination


### chown
	-change file owner and group

### chown -R <insert name>:<insert group>  <insert location>
	-Changes the file owner and group to a specific location
	- https://askubuntu.com/questions/40850/how-can-i-become-the-owner-of-a-file-folder-that-root-owns/40854

### chmod
	-change file mode bits
	- How to use chmod:
		-http://www.thegeekstuff.com/2010/06/chmod-command-examples

### wget
	- Wget is a free utility for non-interactive download of files from
       the Web.

### passwd
	- changes password of login?

### sudo netstat -tlpn
-looks at where all the ports are being listened on?


### sudo rm -rf folderName
- Removes folder and files from ... shit
- http://bit.ly/2oimiSH   

### du -hsc *
- Checks the file sizes of folders and files in the current directory

## Encryption
---------------------------------
### sudo certbot --apache -d example.com
- creates an encryption for your website


## Apache
---------------------------------

### service apache2 reload
	- enable our sites that we created in the conf file

### service apache2 restart
	-restarts the service so that the changes will take effect

### sudo a2dissite <insert conf file>
	- disables sites for apache default.conf

### sudo a2ensite example.conf
- enables the site for apache
- you can also do **sudo apache2 reload example.conf** ,
I think it is preferred

### sudo service apache2 status
- Checks the status of apache
