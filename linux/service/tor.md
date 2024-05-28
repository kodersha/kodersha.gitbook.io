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

Установите пакеты:

{% code overflow="wrap" %}
```bash
yay -S tor lyrebird-proxy
```
{% endcode %}

{% tabs %}
{% tab title="Отредактируйте torrc" %}
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

Создайте пользователя:

{% code overflow="wrap" %}
```bash
sudo useradd -m -d /var/lib/tor -s /bin/false toruser
sudo chown -R toruser:toruser /var/lib/tor
sudo chmod 700 /var/lib/tor
```
{% endcode %}

Отредактируйте `tor.service`:

{% code overflow="wrap" %}
```bash
sudo nano /lib/systemd/system/tor.service
```
{% endcode %}

Добавьте пользователя в раздел`[Service]`:

```systemd
[Service]
User=toruser
Group=toruser
```

***

Перезапутите `systemd`:

{% code overflow="wrap" %}
```bash
sudo systemctl daemon-reload
```
{% endcode %}

Запустите `tor` сервис:

{% code overflow="wrap" %}
```bash
sudo systemctl enable --now tor
```
{% endcode %}

Проверьте состояние:

```bash
sudo systemctl status tor
```



{% code title="Хост подключения SOCKS" overflow="wrap" %}
```
127.0.0.1:9050
```
{% endcode %}
