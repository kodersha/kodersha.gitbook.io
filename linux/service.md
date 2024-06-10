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
    visible: false
---

# Сервисы

### tor

{% code title="Установите tor" overflow="wrap" %}
```bash
sudo pacman -S tor
```
{% endcode %}

```bash
yay -S obfs4proxy
```

***

{% code title="Назначьте пользователя" overflow="wrap" %}
```bash
sudo chown -R tor:tor /var/lib/tor
```
{% endcode %}

{% code title="Обновите права на папку" overflow="wrap" %}
```bash
sudo chmod -R 700 /var/lib/tor
```
{% endcode %}

{% code title="Отредактируйте tor.service" overflow="wrap" %}
```bash
sudo nano /lib/systemd/system/tor.service
```
{% endcode %}

Добавьте пользователя в раздел `[Service]`:

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

{% code title="Обновите конфигурацию" overflow="wrap" %}
```bash
sudo systemctl daemon-reload
```
{% endcode %}

{% code title="Запустите tor сервис" overflow="wrap" %}
```bash
sudo systemctl enable --now tor
```
{% endcode %}

{% code title="Проверьте состояние" overflow="wrap" %}
```bash
sudo systemctl status tor
```
{% endcode %}

{% code title="Хост подключения SOCKS5" overflow="wrap" %}
```bash
127.0.0.1:9050
```
{% endcode %}
