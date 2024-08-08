# Cpanel can't issue a new hostname ssl

#### If you run the following, does it report the correct IP for the server's hostname?

```sh
/scripts/cpdig your.servers.hostname A
```

#### Then run this command:

```sh
whmapi1 adddns domain=your.server's.hostname ip=IP
```

#### Just edit that hostname to yours and the IP as well and then run the command.

Or

#### Run this command

```sh
usr/local/cpanel/bin/checkallsslcerts --verbose
```
