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

Установите пакеты

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
```
{% endcode %}

{% code overflow="wrap" %}
```bash
yay -S obfs4proxy
```
{% endcode %}
{% endtab %}
{% endtabs %}

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

{% tabs %}
{% tab title="fedora" %}
#### Отключите SeLinux

Проверьте, установлено ли для SeLinux значение `enforcing`:

```bash
getenforce
```

Если установлено значение `enforcing`, измените статус на `permissive`:

```bash
sudo setenforce 0
```

Чтобы сделать изменения постоянными:

<pre class="language-bash"><code class="lang-bash"><strong>sudo nano /etc/selinux/config
</strong></code></pre>

И измените `SELINUX=enforcing` на `SELINUX=permissive`.



#### Откройте порты в брандмауэре Fedora

Для obfs4 в файле torrc:

```bash
sudo firewall-cmd --add-port 9050/tcp --permanent
```

После выполните команду:

```bash
sudo firewall-cmd --reload
```
{% endtab %}

{% tab title="arch" %}
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
{% endtab %}
{% endtabs %}

Перезапутите systemd

{% code overflow="wrap" %}
```bash
sudo systemctl daemon-reload
```
{% endcode %}

Запустите tor сервис

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash"><strong>sudo systemctl enable --now tor
</strong></code></pre>



{% code title="Хост подключения SOCKS" overflow="wrap" %}
```
127.0.0.1:9050
```
{% endcode %}
