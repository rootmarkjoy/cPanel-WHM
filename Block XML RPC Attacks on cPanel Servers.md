### Howto Block XML RPC Attacks on cPanel/WHM Servers using CSF

Method 1 – Globally Disable using CSF to Block XML RPC and wp-login Attacks

1) Edit CSF Config either via WHM or SSH through your favourite editor:

```sh
nano /etc/csf/csf.conf
```

locate the line:

```sh
vCUSTOM1_LOG = "/var/log/customlog"
```

and replace it with:

```sh
vCUSTOM1_LOG = "/usr/local/apache/domlogs/*/*"
```

2) Create a function within CSF to detect and block these attacks.

```sh
nano /usr/local/csf/bin/regex.custom.pm
```

Add the following:

```sh
# Block IP if more than 10 requests in 3600 for wp-login
if (($globlogs{CUSTOM1_LOG}{$lgfile}) and ($line =~ /(\S+).*] "\w*(?:GET|POST) \/wp-login\.php.*" /)) {
return ("WP Login Attack",$1,"WPLOGIN","10","80,443","1");
}

# Block IP if more than 10 requests in 3600 for xml-rpc
if (($globlogs{CUSTOM1_LOG}{$lgfile}) and ($line =~ /(\S+).*] "\w*(?:GET|POST) \/xmlrpc\.php.*" /)) {
return ("WP XMLPRC Attack",$1,"XMLRPC","10","80,443","1");
}
```

3) Restart CSF and LFD to apply changed:

```sh
csf -r
service lfd restart
```

Method 2 – Completely disable XML RPC attacks on a per account basis with cPanel using .htaccess

1) Login to your cPanel account and goto the File Manager

2) Goto the public_html directory where your files are located, if your WordPress is installed within this directory then take a backup copy of the .htaccess within this directory, else navigate to your WordPress directory and backup the .htaccess there.

3) If you don’t see the file it is probably because it’s hidden and you need to change the display settings to display hidden files by navigating to the gearbox icon from the top-right corner.

4) Right click the .htaccess file and click edit and add the following:

```sh
# Block XML-RPC 
<Files xmlrpc.php> 
order deny,allow 
deny from all 
</Files>
```

5) Access to your xmlrpc file is now completely disabled, if you need to allow access from specific IPs just add the following below the last </Files> line.

```sh
allow from 8.8.8.8
```

Replacing 8.8.8.8 with the IP you want to access from.
