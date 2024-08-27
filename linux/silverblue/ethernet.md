# 🔮 Интернет

### COMSS dns

{% tabs %}
{% tab title="00-custom.conf" %}
{% code overflow="wrap" %}
```bash
sudo mkdir /etc/systemd/resolved.conf.d && sudo nano /etc/systemd/resolved.conf.d/00-custom.conf
```
{% endcode %}
{% endtab %}

{% tab title="→" %}
```ini
[Resolve]
DNS=76.76.2.22#comss.dns.controld.com
DNSOverTLS=yes
```
{% endtab %}
{% endtabs %}

Также добавьте в `hosts`:

{% tabs %}
{% tab title="hosts" %}
{% code overflow="wrap" %}
```bash
sudo nano /etc/hosts
```
{% endcode %}
{% endtab %}

{% tab title="→" %}
<pre class="language-ini"><code class="lang-ini">127.0.1.1   <a data-footnote-ref href="#user-content-fn-1">fedora</a>
</code></pre>
{% endtab %}
{% endtabs %}

Проверить состояние можно на [controld.com/status](https://controld.com/status).



### spoofDPI

{% code overflow="wrap" %}
```bash
brew install spoofdpi
```
{% endcode %}

Запустите сервис:

{% code overflow="wrap" %}
```bash
brew services start spoofdpi
```
{% endcode %}



### tor

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

{% tabs %}
{% tab title="torrc" %}
{% code overflow="wrap" %}
```bash
nano /home/linuxbrew/.linuxbrew/etc/tor/torrc
```
{% endcode %}
{% endtab %}

{% tab title="→" %}
```ini
## Конфигурация tor для использования мостов

# Разрешить использование мостов
UseBridges 1

# Указание, как Tor должен интерактивно подключаться к мостам с использованием obfs4
ClientTransportPlugin obfs4 exec /home/linuxbrew/.linuxbrew/bin/obfs4proxy

# Добавление моста obfs4
Bridge

# Не запускать Tor в режиме сервиса
RunAsDaemon 0

# SOCKS-порт
SocksPort 9050

DataDirectory /home/linuxbrew/.linuxbrew/var/lib/tor
```
{% endtab %}
{% endtabs %}

Запустите сервис:

{% code overflow="wrap" %}
```bash
brew services start tor
```
{% endcode %}

Адрес хоста подключения SOCKS5: `127.0.0.1:9050`



### zapret

{% code overflow="wrap" %}
```bash
git clone --depth 1 https://github.com/bol-van/zapret && cd zapret && ./install_bin.sh && ./install_prereq.sh
```
{% endcode %}

При необходимости запустите тест:

{% code overflow="wrap" %}
```bash
./blockcheck.sh
```
{% endcode %}

Установите сервис игнорируя предупреждения установщика:

{% code overflow="wrap" %}
```bash
./install_easy.sh
```
{% endcode %}

<details>

<summary>Конфигурация</summary>

Пример конфигурации. Используется `nftables` с `nfqws`.

{% code title="/opt/zapret/config" %}
```ini
# this file is included from init scripts
# change values here

# can help in case /tmp has not enough space
#TMPDIR=/opt/zapret/tmp

# redefine user for zapret daemons. required on Keenetic
#WS_USER=nobody

# override firewall type : iptables,nftables,ipfw
FWTYPE=nftables

# options for ipsets
# maximum number of elements in sets. also used for nft sets
SET_MAXELEM=522288
# too low hashsize can cause memory allocation errors on low RAM systems , even if RAM is enough
# too large hashsize will waste lots of RAM
IPSET_OPT="hashsize 262144 maxelem $SET_MAXELEM"
# dynamically generate additional ip. $1 = ipset/nfset/table name
#IPSET_HOOK="/etc/zapret.ipset.hook"

# options for ip2net. "-4" or "-6" auto added by ipset create script
IP2NET_OPT4="--prefix-length=22-30 --v4-threshold=3/4"
IP2NET_OPT6="--prefix-length=56-64 --v6-threshold=5"
# options for auto hostlist
AUTOHOSTLIST_RETRANS_THRESHOLD=3
AUTOHOSTLIST_FAIL_THRESHOLD=3
AUTOHOSTLIST_FAIL_TIME=60
# 1 = debug autohostlist positives to ipset/zapret-hosts-auto-debug.log
AUTOHOSTLIST_DEBUGLOG=0

# number of parallel threads for domain list resolves
MDIG_THREADS=30

# ipset/*.sh can compress large lists
GZIP_LISTS=1
# command to reload ip/host lists after update
# comment or leave empty for auto backend selection : ipset or ipfw if present
# on BSD systems with PF no auto reloading happens. you must provide your own command
# set to "-" to disable reload
#LISTS_RELOAD="pfctl -f /etc/pf.conf"

# override ports
#HTTP_PORTS=80-81,85
#HTTPS_PORTS=443,500-501
#QUIC_PORTS=443,444

# CHOOSE OPERATION MODE
# MODE : nfqws,tpws,tpws-socks,filter,custom
# nfqws : nfqws for dpi desync
# tpws : tpws transparent mode
# tpws-socks : tpws socks mode
# filter : no daemon, just create ipset or download hostlist
# custom : custom mode. should modify custom init script and add your own code
MODE=nfqws
# apply fooling to http
MODE_HTTP=0
# for nfqws only. support http keep alives. enable only if DPI checks for http request in any outgoing packet
MODE_HTTP_KEEPALIVE=0
# apply fooling to https
MODE_HTTPS=1
# apply fooling to quic
MODE_QUIC=0
# none,ipset,hostlist,autohostlist
MODE_FILTER=ipset,hostlist

# CHOOSE NFQWS DAEMON OPTIONS for DPI desync mode. run "nfq/nfqws --help" for option list
DESYNC_MARK=0x40000000
DESYNC_MARK_POSTNAT=0x20000000
NFQWS_OPT_DESYNC="--dpi-desync=split2 --dpi-desync-ttl=3 --dpi-desync-fooling=md5sig"
#NFQWS_OPT_DESYNC_HTTP="--dpi-desync=split --dpi-desync-ttl=0 --dpi-desync-fooling=badsum"
#NFQWS_OPT_DESYNC_HTTPS="--wssize=1:6 --dpi-desync=split --dpi-desync-ttl=0 --dpi-desync-fooling=badsum"
#NFQWS_OPT_DESYNC_HTTP6="--dpi-desync=split --dpi-desync-ttl=5 --dpi-desync-fooling=none"
#NFQWS_OPT_DESYNC_HTTPS6="--wssize=1:6 --dpi-desync=split --dpi-desync-ttl=5 --dpi-desync-fooling=none"
NFQWS_OPT_DESYNC_QUIC="--dpi-desync=fake --dpi-desync-repeats=6"
#NFQWS_OPT_DESYNC_QUIC6="--dpi-desync=hopbyhop"

# CHOOSE TPWS DAEMON OPTIONS. run "tpws/tpws --help" for option list
# --hostcase
TPWS_OPT="--split-pos=2 --split-http-req=method --oob"

# openwrt only : donttouch,none,software,hardware
FLOWOFFLOAD=none

# openwrt: specify networks to be treated as LAN. default is "lan"
#OPENWRT_LAN="lan lan2 lan3"
# openwrt: specify networks to be treated as WAN. default wans are interfaces with default route
#OPENWRT_WAN4="wan vpn"
#OPENWRT_WAN6="wan6 vpn6"

# for routers based on desktop linux and macos. has no effect in openwrt.
# CHOOSE LAN and optinally WAN/WAN6 NETWORK INTERFACES
# or leave them commented if its not router
# it's possible to specify multiple interfaces like this : IFACE_LAN="eth0 eth1 eth2"
# if IFACE_WAN6 is not defined it take the value of IFACE_WAN
#IFACE_LAN=
#IFACE_WAN=
#IFACE_WAN6="ipsec0 wireguard0 he_net"

# should start/stop command of init scripts apply firewall rules ?
# not applicable to openwrt with firewall3+iptables
INIT_APPLY_FW=1
# firewall apply hooks
#INIT_FW_PRE_UP_HOOK="/etc/firewall.zapret.hook.pre_up"
#INIT_FW_POST_UP_HOOK="/etc/firewall.zapret.hook.post_up"
#INIT_FW_PRE_DOWN_HOOK="/etc/firewall.zapret.hook.pre_down"
#INIT_FW_POST_DOWN_HOOK="/etc/firewall.zapret.hook.post_down"

# do not work with ipv4
#DISABLE_IPV4=1
# do not work with ipv6
DISABLE_IPV6=1

# select which init script will be used to get ip or host list
# possible values : get_user.sh get_antizapret.sh get_combined.sh get_reestr.sh get_hostlist.sh
# comment if not required
GETLIST=get_antifilter_ipsmart.sh
```
{% endcode %}

</details>



Отключите firewalld:

{% code overflow="wrap" %}
```bash
sudo systemctl disable firewalld
```
{% endcode %}

Настройте службу:

{% tabs %}
{% tab title="rc.local" %}
{% code overflow="wrap" %}
```bash
sudo nano /etc/rc.d/rc.local && sudo chmod 755 /etc/rc.d/rc.local
```
{% endcode %}
{% endtab %}

{% tab title="→" %}
{% code overflow="wrap" %}
```bash
#!/bin/bash

exec bash /opt/zapret/init.d/sysv/zapret start
```
{% endcode %}
{% endtab %}
{% endtabs %}

Создайте файл сервиса:

{% tabs %}
{% tab title="rc-local.service" %}
{% code overflow="wrap" %}
```bash
sudo nano /etc/systemd/system/rc-local.service
```
{% endcode %}
{% endtab %}

{% tab title="→" %}
```ini
[Unit]
Description=Compatibility rc.local
ConditionPathExists=/etc/rc.d/rc.local

[Service]
Type=forking
ExecStart=/etc/rc.d/rc.local
TimeoutSec=0
StandardOutput=tty
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target
```
{% endtab %}
{% endtabs %}

Запустите сервис:

{% code overflow="wrap" %}
```bash
sudo systemctl daemon-reload && sudo systemctl enable --now rc-local.service
```
{% endcode %}

#### Список `url` для обхода замедления youtube

{% tabs %}
{% tab title="zapret-hosts-user.txt" %}
{% code overflow="wrap" %}
```bash
sudo nano /opt/zapret/ipset/zapret-hosts-user.txt
```
{% endcode %}
{% endtab %}

{% tab title="→" %}
{% code overflow="wrap" %}
```
googlevideo.com
googleapis.com
i.ytimg.com
i9.ytimg.com
wide-youtube.l.google.com
youtu.be
youtube.com
youtube.googleapis.com
yt3.ggpht.com
yt3.googleusercontent.com
```
{% endcode %}
{% endtab %}
{% endtabs %}

[^1]: Ваш hostname
