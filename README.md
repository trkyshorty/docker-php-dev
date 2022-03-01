# Php Development Environment


## Project Structure

```
bucket\               # Core Folder
 |--services\         # Required services are configured here
    |--mysql\         # mariadb:10.7.3
    |--nginx\         # nginx:1.19.3
    |--php\           # php:8.1-fpm
    |--redis\         # redis:alpine
public\               # Development Folder
 |--phpinfo.php       # Php Version
```

## Requirements

- Docker

## Installation

```bash
# Clone the repo
git clone https://github.com/trkyshorty/docker-php-dev && cd docker-php-dev

# Create & update relevant config
cp .env.example .env

# Start the environment
docker-compose up -d

```

## Updating

Open a terminal window, browse to this project's folder and run:

```bash
# 1. Pull from Git
git pull
# 2. Erase previous containers
docker-compose down --remove-orphans
# 3. Get latest docker images
docker-compose pull
# 4. Rebuild Dockerfiles from scratch (inc. pull parent images)
docker-compose build --pull --no-cache --parallel
# 5. Start the new env
docker-compose up -d
# 6. Erase any unused containers, images, volumes etc. to free disk space.
docker system prune --volumes
```
