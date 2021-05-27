# HDM Network Website #

## Table of content
  - [Installation](#installation)
    - [DOCKER](#docker)
    - [YARN](#yarn)


## How to run locally #

- type `docker network create hdmnetwork`
- In hdm-network-website/ type `docker-compose up -d --build`
- Add hdmnetwork.com to your local hosts `127.0.0.1 hdmnetwork.com`, in the case you do not use Windows for Docker, you might to add the host that way `192.168.99.100 hdmnetwork.com`
- Go to http://hdmnetwork.com and enjoy! (or `localhost:[Port of Nginx] Port of Nginx == (docker ps) port->80`)

For some reason, on Windows you might need to use `192.168.99.100 hdmnetwork.com` instead of `127.0.0.1`

----
## How to run symfony console
``` 
docker-compose exec php-fpm php backend/bin/console
```

## Installation #
