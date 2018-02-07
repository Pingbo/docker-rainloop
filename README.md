Docker Rainloop
=============

Forked from https://github.com/peperunas/docker-rainloop

Working now with Let's Encrypt

Rainloop web client Docker image using nginx (SSL).

How to use
-------

	docker pull pingbo/rainloop-ssl
	docker run -d --name rainloop -v LetsEncrypt/live:/etc/ssl -h rainloop -p 443:443 pingbo/rainloop

Example with Jwilder's NGINX Proxy and Lets Encrypt
-------

  rainloop:
    image: pingbo/rainloop
    container_name: rainloop
    environment:
    - VIRTUAL_HOST=mail.domain.tld
    - VIRTUAL_PROTO=https
    - VIRTUAL_PORT=443
    - LETSENCRYPT_HOST=mail.domain.tld
    - LETSENCRYPT_EMAIL=foo@bar
    volumes:
    - path/to/rainloop/data:/webapps/rainloop/data
    - path/to/letsencrypt/mail.domain.tld/:/etc/ssl/
    ports:
    - "443:443"
    network_mode: bridge

Open your browser and visit 
	
	https://127.0.0.1

Data Persistance
----------------
Mount your data folder to `/webapps/rainloop/data`.


License
-------

Apache 2 http://en.wikipedia.org/wiki/Apache_License

Credits
-------

I've initially modified the Dockerfile of [ahmet2mir](https://github.com/ahmet2mir).
