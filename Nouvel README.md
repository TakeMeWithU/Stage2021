# HDM Network Website 

## Table of content
- [1 Installation](#1-installation)
  - [1-1 DOCKER](#1-1-docker)
  - [1-2 YARN](#1-2-yarn)
- [2 Download Resources](#2-download-resources)
- [3 Setup project](#3-setup-project)
  - [3-1 HDM-Network-Docker](#3-1-hdm-network-docker)
  - [3-2 Website](#3-2-website)
  - [3-3 Ui-Dashboard](3-3-ui-dashboard)
- [4 How to run locally](#4-how-to-run-locally)
  - [4-1 Website](#4-1-website)
  - [4-2 Ui-Dashboard](#4-2-ui-dashboard)
- [5 How to run symfony console](#5-how-to-run-symfony-console)
- [6 Issues](#6-issues)

## 1 Installation
  - This guide is only available for Linux.

  ### 1-1 Docker
  - Install Docker Engine on Ubuntu. Please read and follow this [page](https://docs.docker.com/engine/install/ubuntu/) for install Docker.

  ### 1-2 Yarn
  - Before you start using Yarn, you'll first need to install it on your system. There are many different ways to install Yarn, but a single one is recommended and cross-platform: 
  - Install via npm. Please follow this [guide](https://classic.yarnpkg.com/en/docs/install/#debian-stable).

----
## 2 Download Resources
  - Before you start setting up this project, you'll need to download 3 folders:
    - [HDM-Network-docker](https://github.com/hdm-infra/hdmnetwork-docker).
    - [Website-Frontend](https://github.com/hdmnetwork/website).
    - [Ui-Dashboard-Backend](https://github.com/hdmnetwork/ui-dashboard)
      - *Please contact your leader to all permissions.

----

## 3 Setup project
- Please pay attention to the following:

### 3-1 HDM-Network-Docker
- Create file .env with/or duplicate with .env.examples or juste rename .env.examples to .env
- Change path to your folder Website in file .env:

```
PROJECT_WEBSITE_PATH=/home/{path}
```

- Delete the 3 lines in /nginx/default.conf to run locally:
```
if ( $host !~ ^www\. ) {
  return 301 $scheme://www.$host$request_uri;
}
```

### 3-2 Website
- Create file .env with/or duplicate with .env.test or juste rename .env.test to .env

### 3-3 Ui-Dashboard
- Create file .env.js in public/ with/or duplicate with .env.example.js or juste rename .env.example.js to .env.js

----
## 4 How to run locally

### 4-1 Website
- type `cd hdmnetwork-docker/` or move to folder hdmnetwork-docker/
- type `docker network create hdmnetwork`
- type `docker volume create database-hdmnetwork`
- type `docker-compose up -d --build`

- type `docker ps` to get port of nginx! You need to have 3 deployed containers. If you don't have 3 deployed containers, please wait few seconds or retype `docker-compose up -d --build`.
- Example :
```
CONTAINER ID   IMAGE                           COMMAND                  CREATED             STATUS             PORTS                                         NAMES
3b8f651de4cb   hdmnetwork_php-fpm-hdmnetwork   "docker-php-entrypoi…"   About an hour ago   Up About an hour   0.0.0.0:49159->9000/tcp, :::49159->9000/tcp   php-fpm-hdmnetwork
b3e25668d1e9   hdmnetwork_nginx-hdmnetwork     "/docker-entrypoint.…"   About an hour ago   Up About an hour   0.0.0.0:49160->80/tcp, :::49160->80/tcp       nginx-hdmnetwork
9bf44e0d5709   mysql:5.7.18                    "docker-entrypoint.s…"   About an hour ago   Up About an hour   0.0.0.0:49157->3306/tcp, :::49157->3306/tcp   database-hdmnetwork
```
- In this case, we have 49160 like port of Nginx.

- Don't forget to fixtures your BDD with this commands:
```
docker exec -it php-fpm-hdmnetwork php bin/console doctrine:fixtures:load
```

- Go to `localhost:[Port of Nginx] Port of Nginx == (docker ps) port->80` and enjoy!


### 4-2 Ui-Dashboard
- type `cd ui-dashboard` or move to folder ui-dashboard/

- Change settings in file .env.js: 
```
(function () {
  window.hdm_env = window.hdm_env || {};
  window.hdm_env.REACT_APP_API_URL = 'http://hdmnetwork.com';
  window.hdm_env.REACT_APP_MEDIA_URL = 'http://hdmnetwork.com/media/';
  window.hdm_env.REACT_APP_MEDIA_URL_JOBS = 'http://hdmnetwork.com/assets/images/jobs/'; 
})();
```

- In the case, we have 49160 like port of nginx:
```
(function () {
  window.hdm_env = window.hdm_env || {};
  window.hdm_env.REACT_APP_API_URL = "http://localhost:49160/";
  window.hdm_env.REACT_APP_MEDIA_URL = "http://localhost:49160/media/";
  window.hdm_env.REACT_APP_MEDIA_URL_JOBS = 'http://localhost:49160/assets/images/jobs/'; 
})();
```

- type `yarn install`
- type `yarn start`
- For another commands, you can read file README.md in folder ui-dashboard.

----
## 5 How to run symfony console
``` 
docker exec -it php-fpm-hdmnetwork [commands]
```

- Example:
``` 
docker exec -it php-fpm-hdmnetwork php bin/console 
```

## 6 Issues
 -  Please check closed issues before asking in IT channel.
 -  [Website](https://github.com/hdmnetwork/website/issues)
 -  [Ui-Dasboard](https://github.com/hdmnetwork/ui-dashboard/issues)
  
 - If you cannot find the solution for your problem. Please ask your team and create a new issue with/without solution.
