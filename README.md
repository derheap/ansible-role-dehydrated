# Let’s encrypt/acme-tiny role for Ansible

Forked from https://github.com/andreaswolf/ansible-role-letsencrypt.

Tutorials

* https://www.aaflalo.me/2016/09/dehydrated-bash-client-lets-encrypt/

## Nginx Config

~~~~
server {
    listen 80 default_server;

    server_name DOMAIN;
    root DOCROOT;

    location /.well-known/acme-challenge {
      alias /var/www/dehydrated;
      allow all;
    }

    location / {
        return 301 https://$host$request_uri;
    }
}
~~~~

In the SSL section:

~~~~
server {

    listen 443 ssl default_server;

    ssl_certificate /etc/dehydrated/certs/ask23.de/fullchain.pem;
    ssl_certificate_key /etc/dehydrated/certs/ask23.de/privkey.pem;

    include /etc/letsencrypt/options-ssl-nginx.conf;
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem;
 # ...
}
~~~~

## License

MIT


## Author Information


