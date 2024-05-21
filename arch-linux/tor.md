# Тор

{% code title="Установка пакетов" overflow="wrap" %}
```bash
sudo pacman -S tor
yay -S obfs4proxy
```
{% endcode %}

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
## Пример конфигурации Tor для использования мостов

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

# Журналирование информации для отладки
Log notice file /var/log/tor/notices.log
```
{% endtab %}
{% endtabs %}

{% code title="Создание пользователя" overflow="wrap" %}
```bash
sudo useradd -m -d /var/lib/tor -s /bin/false toruser
sudo chown -R toruser:toruser /var/lib/tor
sudo chmod 700 /var/lib/tor
```
{% endcode %}

{% tabs %}
{% tab title="Конфигурация tor.service" %}
{% code overflow="wrap" %}
```bash
sudo nano /lib/systemd/system/tor.service
```
{% endcode %}
{% endtab %}

{% tab title="→" %}
```systemd
[Service]
User=toruser
Group=toruser
```
{% endtab %}
{% endtabs %}

{% code title="Перезапуск systemd" overflow="wrap" %}
```bash
sudo systemctl daemon-reload
```
{% endcode %}

{% code title="Запуск сервиса" overflow="wrap" %}
```bash
sudo systemctl start tor
sudo systemctl enable tor
```
{% endcode %}
