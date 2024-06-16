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

# 🔮 Интернет

### COMSS dns

Установите `curl`

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed curl
```
{% endcode %}

Запустите скрипт автоматической установки:

{% code overflow="wrap" %}
```bash
sudo sh -c 'sh -c "$(curl -sL https://api.controld.com/dl)" -s comss'
```
{% endcode %}

Проверить состояние можно на [controld.com/status](https://controld.com/status).

Для удаления:

```bash
sudo ctrld stop
sudo ctrld uninstall
```

{% embed url="https://www.comss.ru/page.php?id=12918" %}



### tor

Установите `tor` и `obfs4proxy`:

{% tabs %}
{% tab title="tor " %}
{% code overflow="wrap" %}
```bash
sudo pacman -S tor
```
{% endcode %}
{% endtab %}

{% tab title="obfs4proxy" %}
```bash
yay -S obfs4proxy
```
{% endtab %}
{% endtabs %}

Назначьте пользователя и права на папку:

{% code overflow="wrap" %}
```bash
sudo chown -R tor:tor /var/lib/tor && sudo chmod -R 700 /var/lib/tor
```
{% endcode %}

Отредактируйте `tor.service` и добавьте пользователя и группу в раздел `[Service]`:

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

Обновите конфигурацию и запустите `tor` сервис:

{% code overflow="wrap" %}
```bash
sudo systemctl daemon-reload && sudo systemctl enable --now tor
```
{% endcode %}

При необходимости проверьте состояние:

{% code overflow="wrap" %}
```bash
sudo systemctl status tor
```
{% endcode %}

Адрес хоста подключения SOCKS5: `127.0.0.1:9050`
