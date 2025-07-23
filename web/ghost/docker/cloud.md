---
description: Базовая конфигурация для запуска ghost с remark42 на облачном сервере.
---

# cloud

{% code title="docker-compose.yml" lineNumbers="true" %}
```yaml
networks:
  network:
    driver: bridge

services:
  mariadb:
    container_name: ghost_mariadb
    networks:
      - network
    image: mariadb:${MARIADB_IMAGE_TAG}
    environment:
      MYSQL_ROOT_PASSWORD: ${MYSQL_ROOT_PASSWORD}
      MYSQL_USER: ghost
      MYSQL_PASSWORD: ${MYSQL_PASSWORD}
      MYSQL_DATABASE: ghost_production
      MYSQLD_MAX_CONNECTIONS: 200
      MYSQLD_WAIT_TIMEOUT: 28800
      MYSQLD_INTERACTIVE_TIMEOUT: 28800
      MYSQLD_MAX_ALLOWED_PACKET: "128M"
    restart: always
    volumes:
      - type: bind
        source: ${MYSQL_HOST_PATH}
        target: /var/lib/mysql

  ghost:
    build: 
      context: .
    container_name: ghost_ghost
    networks:
      - network
    ports:
      - 8022:2368
    environment:
      url: ${BLOG_URL:-https://example.com}
      database__client: mysql
      database__connection__host: mariadb
      database__connection__database: ghost_production
      database__connection__user: ghost
      database__connection__password: ${MYSQL_PASSWORD}
      imageOptimization__srcsets: false
      imageOptimization__resize: false
    depends_on:
      - mariadb
    restart: always
    volumes:
      - type: bind
        source: ${GHOST_HOST_PATH}
        target: /var/lib/ghost/content

  remark:
    image: umputun/remark42:${REMARK_IMAGE_TAG}
    container_name: ghost_remark
    networks:
      - network
    ports:
      - "8888:8080"
    restart: always
    environment:
      - REMARK_URL=${REMARK_URL:-https://example.com/comments}
      - ALLOWED_HOSTS=https://example.com/
      - SITE=
      - SECRET=
      - AUTH_GITHUB_CID=
      - AUTH_GITHUB_CSEC=
      - AUTH_GOOGLE_CID=
      - AUTH_GOOGLE_CSEC=
      - AUTH_YANDEX_CID=
      - AUTH_YANDEX_CSEC=
      - TELEGRAM_TOKEN=
      - NOTIFY_TELEGRAM_CHAN=
      - AUTH_TELEGRAM=true
      - NOTIFY_ADMINS=telegram
      - IMAGE_MAX_SIZE=50000
      - IMAGE_RESIZE_WIDTH=1920
      - IMAGE_PROXY_HTTP2HTTPS=true
      - EMOJI=true
      - AVATAR_RESIZE=48
      - MAX_BACKUP_FILES=1
      - MIN_COMMENT_SIZE=2
      - VOTES_IP=true
      - ADMIN_SHARED_ID=
      - ADMIN_SHARED_EMAIL=
      - ADMIN_PASSWD=
      - ADMIN_EDIT=true
      - DISABLE_FANCY_HTML_FORMATTING=true
      - SIMPLE_VIEW=true
    volumes:
      - type: bind
        source: ${REMARK_HOST_PATH}
        target: /srv/var

  nginx:
    image: nginx:latest
    container_name: ghost_nginx
    networks:
      - network
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf:ro
      - ./certbot/www:/var/www/certbot
      - ./certbot/conf:/etc/letsencrypt
      - ./www:/ghost
    depends_on:
      - ghost
      - remark

  certbot:
    image: certbot/certbot
    container_name: ghost_certbot
    volumes:
      - ./certbot/conf:/etc/letsencrypt
      - ./certbot/www:/var/www/certbot
```
{% endcode %}

{% code title="Dockerfile" lineNumbers="true" %}
```docker
# Используем базовый образ Ghost
FROM ghost:latest

# Устанавливаем Yarn
USER root
RUN apt-get update && apt-get install -y curl gnupg

# Устанавливаем Node.js через nvm
RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
ENV NVM_DIR="/root/.nvm"
ENV NODE_VERSION="lts/*"
RUN . "$NVM_DIR/nvm.sh" && nvm install $NODE_VERSION && nvm use $NODE_VERSION && \
    nvm alias default $NODE_VERSION && \
    npm install -g yarn

# Переходим обратно от root пользователя к node
USER node
```
{% endcode %}

{% code title=".env" lineNumbers="true" %}
```ini
GHOST_IMAGE_TAG=latest
MARIADB_IMAGE_TAG=latest
REMARK_IMAGE_TAG=latest

BLOG_URL=https://example.com
REMARK_URL=https://example.com/comments

MYSQL_ROOT_PASSWORD=
MYSQL_PASSWORD=

MYSQL_HOST_PATH=./mariadb
GHOST_HOST_PATH=./www
REMARK_HOST_PATH=./remark
```
{% endcode %}

{% code title="nginx.conf" lineNumbers="true" %}
```nginx
events {}

http {
  server {
    listen 80;
    server_name example.com www.example.com;

    # Redirect all HTTP requests to HTTPS
    return 301 https://$host$request_uri;
  }

  server {
    listen 443 ssl;
    server_name example.com www.example.com;

    ssl_certificate /etc/letsencrypt/live/example.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem;

    location / {
      proxy_pass http://ghost:2368;
      proxy_set_header Host $host;
      proxy_set_header X-Real-IP $remote_addr;
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header X-Forwarded-Proto $scheme;
    }

    location /comments/ {
      proxy_pass http://remark:8080/;
      proxy_set_header Host $host;
      proxy_set_header X-Real-IP $remote_addr;
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header X-Forwarded-Proto $scheme;
    }

    # Section for proxying CSS remark file
    # location /comments/web/remark.css {
    #  alias /ghost/themes/undefined/assets/comments.css;
    #  types {
    #    text/css css;
    #  }
    # }
  }
}
```
{% endcode %}
