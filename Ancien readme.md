# No Sense Website #
## How to run locally #

- type `docker network create nosense`
- In website/ type `docker-compose up -d --build`
- Add nosense.news to your local hosts `127.0.0.1 nosense.news`, in the case you do not use Windows for Docker, you might to add the host that way `192.168.99.100 nosense.news` 
- Go to http://nosense.news and enjoy! (or `localhost:[Port of Nginx] Port of Nginx == (docker ps) port->80`)

For some reason, on Windows you might need to use `192.168.99.100 nosense.news` instead of `127.0.0.1`

----
## How to run symfony console
```
docker-compose exec php-fpm php backend/bin/console
```

