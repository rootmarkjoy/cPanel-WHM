### Blocking DDoS attacks on cPanel server IP :443

To block attacks to server_ip and port 443, add the following code to /etc/apache2/conf.d/includes/pre_virtualhost_global.conf

```sh
<VirtualHost IP_HERE:443>
  <Location />
    Deny from all
    Redirect "/" "http://127.0.0.1/"
  </Location>
</VirtualHost>
```

then save and restart apache.

To test, try visiting IP:443 in your browser.
