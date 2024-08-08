# Cloudflare plugin installation for Cpanel:-

#### Run the below Commands on the server:-

```sh
curl -k -L https://github.com/cloudflare/CloudFlare-CPanel/tarball/master > cloudflare.tar.gz
tar -zxvf cloudflare.tar.gz
cd cloudflare-CloudFlare-CPanel-c7350fb/
./cloudflare.install.sh -k 9bebf49978bb09d4273a4bac84e54482 -n "Cloudflare Partner"
```
