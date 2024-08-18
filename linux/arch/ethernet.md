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

Установите `curl`, если его нет

{% code overflow="wrap" %}
```bash
aura -S --needed curl
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

{% code overflow="wrap" %}
```bash
sudo ctrld stop && sudo ctrld uninstall
```
{% endcode %}

{% embed url="https://www.comss.ru/page.php?id=12918" %}



### tor

Установите `tor` и `obfs4proxy`:

{% tabs %}
{% tab title="homebrew" %}
{% code overflow="wrap" %}
```bash
brew install tor obfs4proxy
```
{% endcode %}

Создайте папку для `DataDirectory`:

{% code overflow="wrap" %}
```bash
mkdir /home/linuxbrew/.linuxbrew/var/lib/tor
```
{% endcode %}

Создайте файл конфигурации:

{% code overflow="wrap" %}
```bash
nano /home/linuxbrew/.linuxbrew/etc/tor/torrc
```
{% endcode %}

{% code title="torrc" %}
```ini
## Конфигурация tor для использования мостов

# Разрешить использование мостов
UseBridges 1

# Указание, как Tor должен интерактивно подключаться к мостам с использованием obfs4
ClientTransportPlugin obfs4 exec /home/linuxbrew/.linuxbrew/bin/obfs4proxy

# Добавление мостов obfs4
Bridge # Укажите obfs4 мост

# Не запускать Tor в режиме сервиса
RunAsDaemon 0

# SOCKS-порт
SocksPort 9050

DataDirectory /home/linuxbrew/.linuxbrew/var/lib/tor
```
{% endcode %}

Запустите сервис:

```bash
brew services start tor
```

Адрес хоста подключения SOCKS5: `127.0.0.1:9050`
{% endtab %}

{% tab title="pkg" %}
{% code overflow="wrap" %}
```bash
aura -S tor && aura -A obfs4proxy
```
{% endcode %}

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

{% code overflow="wrap" %}
```editorconfig
[Service]
User=tor
Group=tor
```
{% endcode %}

Конфигурация мостов:

{% code overflow="wrap" %}
```bash
sudo nano /etc/tor/torrc
```
{% endcode %}

{% code title="torrc" %}
```editorconfig
## Конфигурация tor для использования мостов

# Разрешить использование мостов
UseBridges 1

# Указание, как Tor должен интерактивно подключаться к мостам с использованием obfs4
ClientTransportPlugin obfs4 exec /usr/bin/obfs4proxy

# Добавление мостов obfs4
Bridge # Укажите obfs4 мост

# Не запускать Tor в режиме сервиса
RunAsDaemon 0

# SOCKS-порт
SocksPort 9050

DataDirectory /var/lib/tor
```
{% endcode %}

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
{% endtab %}
{% endtabs %}
