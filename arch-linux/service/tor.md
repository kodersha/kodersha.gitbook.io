---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: false
  pagination:
    visible: true
---

# tor

Установка пакетов

{% tabs %}
{% tab title="fedora" %}
```
sudo dnf install tor obfs4
```
{% endtab %}

{% tab title="arch" %}
{% code overflow="wrap" %}
```bash
sudo pacman -S tor
yay -S obfs4proxy
```
{% endcode %}
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Конфигурация torrc" %}
{% code overflow="wrap" %}
```bash
sudo nano /etc/tor/torrc
```
{% endcode %}
{% endtab %}

{% tab title="→" %}
```editorconfig
## Конфигурация tor для использования мостов

# Разрешить использование мостов
UseBridges 1

# Указание, как Tor должен интерактивно подключаться к мостам с использованием obfs4
ClientTransportPlugin obfs4 exec /usr/bin/obfs4proxy

# Добавление мостов obfs4
Bridge obfs4 [...]
Bridge obfs4 [...]
Bridge obfs4 [...]

# Не запускать Tor в режиме сервиса
RunAsDaemon 0

# SOCKS-порт
SocksPort 9050

DataDirectory /var/lib/tor
```
{% endtab %}
{% endtabs %}

<details>

<summary>arch</summary>

Создание пользователя

{% code overflow="wrap" %}
```bash
sudo useradd -m -d /var/lib/tor -s /bin/false toruser
sudo chown -R toruser:toruser /var/lib/tor
sudo chmod 700 /var/lib/tor
```
{% endcode %}

Конфигурация tor.service

{% code overflow="wrap" %}
```bash
sudo nano /lib/systemd/system/tor.service
```
{% endcode %}

```systemd
[Service]
User=toruser
Group=toruser
```

</details>

Перезапуск systemd

{% code overflow="wrap" %}
```bash
sudo systemctl daemon-reload
```
{% endcode %}

Запуск tor сервиса

{% code overflow="wrap" %}
```bash
sudo systemctl start tor
sudo systemctl enable tor
```
{% endcode %}



{% code title="Хост SOCKS" overflow="wrap" %}
```
127.0.0.1:9050
```
{% endcode %}
