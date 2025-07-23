---
description: Конфигурация для запуска на localhost.
---

# local

{% code title="docker-compose.yml" lineNumbers="true" %}
```yaml
version: '3.8'

services:
  php:
    build:
      context: .
      dockerfile: Dockerfile
    container_name: aegea-php
    ports:
      - "80:80"
    volumes:
      - ./src:/var/www/html
    networks:
      - network

  mysql:
    image: mysql:8.0
    container_name: aegea-mysql
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: blogengine
      MYSQL_USER: user
      MYSQL_PASSWORD: user
    volumes:
      - mysql-data:/var/lib/mysql
    networks:
      - network

  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    container_name: aegea-phpmyadmin
    environment:
      PMA_HOST: aegea-mysql
      MYSQL_ROOT_PASSWORD: root
    ports:
      - "8081:80"
    networks:
      - network

volumes:
  mysql-data:

networks:
  network:
    driver: bridge
```
{% endcode %}

{% code title="Dockerfile" lineNumbers="true" %}
```docker
FROM php:8.2-apache

# Расширения
RUN docker-php-ext-install pdo pdo_mysql mysqli

# mod_rewrite
RUN a2enmod rewrite

# Конфигурация Apache
COPY ./apache-config.conf /etc/apache2/sites-available/000-default.conf

# Директория веб-сервера
COPY ./src /var/www/html/

# Права доступа
RUN chown -R www-data:www-data /var/www/html/
```
{% endcode %}

{% code title="apache-config.conf" lineNumbers="true" %}
```apacheconf
<VirtualHost *:80>
  DocumentRoot /var/www/html

  <Directory /var/www/html>
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
  </Directory>
  
  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined

  ServerName localhost
</VirtualHost>
```
{% endcode %}

***

Для Arch linux дать доступ к порту `80`:

{% tabs %}
{% tab title="sysctl.conf" %}
{% code overflow="wrap" %}
```bash
sudo nano /etc/sysctl.conf
```
{% endcode %}
{% endtab %}

{% tab title="→" %}
```ini
net.ipv4.ip_unprivileged_port_start=80
```
{% endtab %}

{% tab title="→" %}
```bash
sudo sysctl -p
```
{% endtab %}
{% endtabs %}
