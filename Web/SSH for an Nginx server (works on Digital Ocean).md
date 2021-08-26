[source](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-20-04#step-5-%E2%80%93-setting-up-server-blocks-(recommended))

Install nginx & certbot

```bash
sudo apt update
sudo apt install nginx
sudo apt install certbot python3-certbot-nginx
```

Verify it's running

```bash
systemctl status nginx
```

Organise domain A record for new domain or subdomain of rupert.cloud on DNS (Vercel probably)

```
A [subdomain or @] [DROPLET IP ADDRESS]
```

Edit configuration & update with domain name, proxy details

```bash
sudo nano /etc/nginx/sites-available/default
```

```nginx
...
server_name [subdomain.domain.com];

location / {
  proxy_pass http://127.0.0.1:[PORT];
}
...
```

where [PORT] is the port of the service running locally. For example, 5005 for Rasa. 

Verify configuration and reload:

```bash
sudo nginx -t
sudo systemctl reload nginx
```

Get SSL certificates & automatically add them to NGINX *(note: if this doesn't work, then you have to make a custom server block file – see [here](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-20-04#step-5-%E2%80%93-setting-up-server-blocks-(recommended)), then adjust configuration step [here](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-20-04))*

```
sudo certbot --nginx -d example.com -d www.example.com
```

Your API should now work over SSL.

(See [this tutorial](https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-18-04) to do the same thing with Apache)