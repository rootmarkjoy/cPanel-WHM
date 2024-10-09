### Server Hardening with ConfigServer Security & Firewall (CSF)

CSF was designed for Linux servers by Way to the Web Limited and is very powerful SPI (Stateful Packet Inspection) iptables firewall script with a Login/Intrusion Detection and Security capabilities like blocking traffic from well known spammers network using the DShield Block List and the Spamhaus DROP List. Below is a small cut of it's features:

- Excessive connection blocking
- Excessive user processes reporting
- SYN Flood protection
- Port Scan tracking and blocking

To help with the ease and flexibility of the suite, CSF has a front-end which could be easily integrated with control panels like cPanel, DirectAdmin and Webmin. This makes configuring and managing the firewall very simple task.

This post describes how to harden your server with CSF: installation, configuration and control panel integration.

The installation process is simple: just download the latest version of CSF from download page, untar it and launch the installation script:

```sh
cd /root/work
wget http://www.configserver.com/free/csf.tgz
tar -xzf csf.tgz
sh csf/install.sh
rm -Rf /root/work/csf*
```

When installation is completed, test whether you have the required iptables modules:

```sh
perl /etc/csf/csftest.pl
```

If everything works, you should get output like this:

```sh
Testing ip_tables/iptable_filter...OK
Testing ipt_LOG...OK
Testing ipt_multiport/xt_multiport...OK
Testing ipt_REJECT...OK
Testing ipt_state/xt_state...OK
Testing ipt_limit/xt_limit...OK
Testing ipt_recent...OK
Testing ipt_owner...OK
Testing iptable_nat/ipt_REDIRECT...OK

RESULT: csf should function on this server
```

Next, backup the original config file /etc/csf/csf.conf, open it and make the following changes:

```sh
AUTO_UPDATES = "1"
LF_DSHIELD = "86400"
LF_SPAMHAUS = "86400"
LF_BOGON = "86400"
```

The basic configuration could be done by modifying in config directives ETH_DEVICE, TCP_IN, TCP_OUT, UDP_IN and UDP_OUT.

Note: In case of bad config, CSF will flush iptables after 5 minutes, because testing mode is enabled by default.

Start CSF and check open TCP and UDP ports with nmap:

```sh
/etc/init.d/csf start
nmap -sSU -F ip.address
```

If check shows that everything is OK, testing mode could be disabled. Edit config file /etc/csf/csf.conf and set:

```sh
TESTING = "0"
```

Now the firewall is fully configured and tested. Restart it:

```sh
/etc/init.d/csf restart
```

https://www.sysadmin.md/server-hardening-with-configserver-security-firewall-csf.html
