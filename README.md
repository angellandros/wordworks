# wordworks
WordWorks is a machine translation project, using BabelNet.

## Install
WordWorks consists of many sub-projects. Each of them must be built separately.

### WordWorks Java
* First download BabelNet version 2.5, API and index, and also download WordNet 3.0.
* Copy `wordworks-java` into your Eclipse workspace.
* Copy `config` and `resources` from BabelNet API project into `wordworks-java`.
* Extract BabelNet index.
* Set `babelnet.dir` in `config/babelnet.var.properties` to your BabelNet index directory.
* Set `jlt.wordnetPrefix` in `config/jlit.var.properties` to your WordNet directory address, without its version. (You can find more instructions in the file.)
* Now you're good to go. You can run examples with Eclipse, or build the project with Maven.

### WordWorks PHP
First way, is easiest when you just want to use the code.
* Copy files in `wordworks-php` into a folder in your Apache HTTP Server working directory, e.g. `wordworks-ui` in `htdocs` for XAMPP.
* Start your Apache Server.
* Open your browser and go to `127.0.0.1/wordworks-ui/wordcloud.php`.
* Now you're good to go.

If you want to develop too, it is easier to do this.
For Windows, we assume that your project directory is `B:/Documents/Dev/Git/git/wordworks`.
* Go to `xampp/apache/conf/extra/httpd-vhosts.conf`.
* Uncomment line 19 (`NameVirtualHost *:80`).
* Uncomment the block starting at line ~36, and change it to this:

	```
	<VirtualHost *:80>
		DocumentRoot "B:/Documents/Dev/Git/git/wordworks"
		ServerName wordworks.localhost
		<Directory B:/Documents/Dev/Git/git/wordworks>
			Order allow,deny
			Allow from all
		</Directory>
	</VirtualHost>
	```

* Save it.
* Go to `Windows/System32/drivers/etc/hosts`.
* Add `127.0.0.1		wordworks.localhost` to the end of file (before the Spybot - Search & Destroy stuff if you have that installed).
* Save it. (You might have to save it to the desktop, change the permissions on the old hosts file (right click > properties), and copy the new one into the directory over the old one (or rename the old one) if you are using Vista and have trouble).
* Restart Apache.
* Go to `localhost/wordworks-php`.

If it says `Access forbidden!`, go to `httpd.conf` and find `<Directory />`. Then replace the whole block with this:
```
<Directory />
    Options FollowSymLinks
    AllowOverride All
    Order deny,allow
    Allow from all
</Directory>
```
Restart Apache, and you're good to go.