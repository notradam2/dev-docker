# About
This repo is intended to set up a docker compose in your local development environment.

# Requirements
- Docker for Mac or Linux
- docker-compose

# Docker Setup
### Docker Cloning
Git clone this repository
```
git clone git@github.com:notradam2/dev-docker.git

cd dev-docker
```

### Hosts settings

Please additionally write the content of `hosts` into your `/etc/hosts`.

```
cat hosts
sudo vim /etc/hosts
```

### Clone application repo

Please `git clone` the project you need in `apps` folder.  


### Docker-compose build

```
cd ~/projects/dev-docker
docker-compose build && docker-compose up -d

# Check active containers.
docker ps
```


### Create Database

Please create a database for your project.
(or you can just use MySQLWorkbench to create a database)
```
docker exec -it instabook-db bash
mysql -u root -padmin

CREATE DATABASE instabook_db DEFAULT CHARACTER SET utf8mb4;
```
