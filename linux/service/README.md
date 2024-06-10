---
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# Сервисы

### tor

Установите tor и obfs4proxy:

{% code overflow="wrap" %}
```bash
sudo pacman -S tor
```
{% endcode %}

```bash
yay -S obfs4proxy
```

***

Назначьте пользователя и права на папку:

{% code overflow="wrap" %}
```bash
sudo chown -R tor:tor /var/lib/tor
sudo chmod -R 700 /var/lib/tor
```
{% endcode %}

Отредактируйте tor.service и добавьте пользователя и группу в раздел `[Service]`:

{% code overflow="wrap" %}
```bash
sudo nano /lib/systemd/system/tor.service
```
{% endcode %}

```editorconfig
[Service]
User=tor
Group=tor
```

***

Конфигурация мостов:

{% tabs %}
{% tab title="torrc" %}
```bash
sudo nano /etc/tor/torrc
```
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

***

Обновите конфигурацию и запустите tor сервис:

{% code overflow="wrap" %}
```bash
sudo systemctl daemon-reload
```
{% endcode %}

{% code overflow="wrap" %}
```bash
sudo systemctl enable --now tor
```
{% endcode %}

При необходимости проверьте состояние:

{% code overflow="wrap" %}
```bash
sudo systemctl status tor
```
{% endcode %}

Адрес хоста подключения SOCKS5:

{% code overflow="wrap" %}
```bash
127.0.0.1:9050
```
{% endcode %}
