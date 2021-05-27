# HDM Network Website 

## Table of content
- [1 Installation](#1-installation)
  - [1.1 DOCKER](#1-1-docker)
  - [1.2 YARN](#1-2-yarn)
- [Download Resources](#download-resources)
- [Setup project](#setup-project)
  - [HDM-Network-Docker](#hdm-network-docker)

## 1 Installation
  - This guide is only available for Linux.

  ### 1-1 Docker
  - Install Docker Engine on Ubuntu. Please read and follow this [page](https://docs.docker.com/engine/install/ubuntu/) for install Docker.

  ### 1-2 Yarn
  - Before you start using Yarn, you'll first need to install it on your system. There are many different ways to install Yarn, but a single one is recommended and cross-platform: 
  - Install via npm. Please follow this [guide](https://classic.yarnpkg.com/en/docs/install/#debian-stable).

## Download Resources
  - Before you start setting up this project, you'll need to download 3 foldes:
    - [HDM-Network-docker](https://github.com/hdm-infra/hdmnetwork-docker).
    - [Website-Frontend](https://github.com/hdmnetwork/website).
    - [Ui-Dashboard-Backend](https://github.com/hdmnetwork/ui-dashboard)
      - *Please contact your leader to all permissions.

## Setup project
- Please pay attention to the following:

### HDM-Network-Docker
- Create file .env in duplicate with .env.examples or juste rename .env.examples to .env
- Change path to your folder Website in file .env:

```
PROJECT_WEBSITE_PATH=/home/{path}
```

## How to run locally

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
