### How to Install and Use Imapsync on CentOS & Fedora

### Imapsync package is available under EPEL package repository. First make sure you have added EPEL on your system or install it first.
```sh
$  sudo yum install epel-release
```

### Now, install imapsync package using following command.
```sh
$ sudo yum install imapsync
```

At this stage, your system is ready for migration all data from one email account to other email accounts using IMAP.

### Transfer Emails with IMAP
## So you are ready for migration. Before migration make sure both accounts have IMAP running and accessible from your system. After that use following command syntax.

```sh
$ imapsync --host1 imap.source.example.com  \
	   --user1 user@example.com 	    \
	   --password1 S0urcePassw0rd  	    \
	   --ssl1			    \
	   --host2 imap.dest.example.com    \
	   --user2 user@example.com 	    \
	   --password2 Dest1nat10NPassw0rd  \
	   --ssl2
```

```sh
imapsync --host1 <domain.com> --user1 <source@domain.com> --ssl1 --password1 <source.password> --host2 <198.168.137.178> --user2 <detination@domain.com> --ssl2 --password2 <detination.password>
```
