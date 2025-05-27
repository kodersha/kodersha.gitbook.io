---
icon: router
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# Интернет

### tor

{% stepper %}
{% step %}
Установите `tor` и `obfs4proxy`:

{% code overflow="wrap" %}
```bash
aura -S tor && aura -A obfs4proxy
```
{% endcode %}
{% endstep %}

{% step %}
Назначьте пользователя и права на папку:

{% code overflow="wrap" %}
```bash
sudo chown -R tor:tor /var/lib/tor && sudo chmod -R 700 /var/lib/tor
```
{% endcode %}
{% endstep %}

{% step %}
Отредактируйте `tor.service`:

{% code overflow="wrap" %}
```bash
sudo nano /lib/systemd/system/tor.service
```
{% endcode %}
{% endstep %}

{% step %}
Добавьте пользователя и группу в раздел `[Service]`:

{% code overflow="wrap" %}
```editorconfig
[Service]
User=tor
Group=tor
```
{% endcode %}
{% endstep %}

{% step %}
Конфигурация мостов:

{% code overflow="wrap" %}
```bash
sudo nano /etc/tor/torrc
```
{% endcode %}
{% endstep %}

{% step %}
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
{% endstep %}

{% step %}
Запустите `tor` сервис:

{% code overflow="wrap" %}
```bash
sudo systemctl daemon-reload && sudo systemctl enable --now tor
```
{% endcode %}
{% endstep %}

{% step %}
При необходимости проверьте состояние:

{% code overflow="wrap" %}
```bash
sudo systemctl status tor
```
{% endcode %}
{% endstep %}
{% endstepper %}

Адрес хоста подключения SOCKS5: `127.0.0.1:9050`



### zapret

#### Автоматическая настройка <a href="#zapret-auto" id="zapret-auto"></a>

{% stepper %}
{% step %}
Клонируйте репозиторий:

{% code overflow="wrap" %}
```bash
git clone https://github.com/Sergeydigl3/zapret-discord-youtube-linux.git
```
{% endcode %}
{% endstep %}

{% step %}
Перейдите в папку:

{% code overflow="wrap" %}
```bash
mv zapret-discord-youtube-linux .zapret && cd .zapret
```
{% endcode %}
{% endstep %}

{% step %}
Запустите скрипт:

{% code overflow="wrap" %}
```bash
sudo bash main_script.sh
```
{% endcode %}
{% endstep %}

{% step %}
Следуйте предложенным шагам - выберете ваше интернет соединение и стратегию.&#x20;
{% endstep %}

{% step %}
Проверьте работоспособность, затем остановите скрипт <kbd>Ctrl</kbd> + <kbd>C</kbd>.
{% endstep %}

{% step %}
Запустите скрипт установки сервиса:

{% code overflow="wrap" %}
```bash
sudo bash service.sh
```
{% endcode %}
{% endstep %}
{% endstepper %}

{% embed url="https://github.com/Sergeydigl3/zapret-discord-youtube-linux/tree/stable2" %}



#### Ручная настройка <a href="#zapret-manual" id="zapret-manual"></a>

{% hint style="danger" %}
Это лишь пример базовой настройки и запуска сервиса. Конфигурация может быть устаревшей.
{% endhint %}

{% stepper %}
{% step %}
{% code overflow="wrap" %}
```bash
wget -qO- https://github.com/bol-van/zapret/releases/download/v69.9/zapret-v69.9.tar.gz | tar -xvz && cd zapret-v69.9 && ./install_bin.sh && ./install_prereq.sh
```
{% endcode %}
{% endstep %}

{% step %}
При необходимости запустите тест соединения:

{% code overflow="wrap" %}
```bash
./blockcheck.sh
```
{% endcode %}
{% endstep %}

{% step %}
Установите сервис:

{% code overflow="wrap" %}
```bash
./install_easy.sh
```
{% endcode %}
{% endstep %}

{% step %}
Отредактируйте конфигурацию:

{% code overflow="wrap" %}
```bash
sudo nano /opt/zapret/config
```
{% endcode %}
{% endstep %}

{% step %}
Пример конфигурации:

{% code title="/opt/zapret/config" %}
```ini
# this file is included from init scripts
# change values here

# can help in case /tmp has not enough space
#TMPDIR=/opt/zapret/tmp

# redefine user for zapret daemons. required on Keenetic
#WS_USER=nobody

# override firewall type : iptables,nftables,ipfw
#FWTYPE=iptables
# nftables only : set this to 0 to use pre-nat mode. default is post-nat.
# pre-nat mode disables some bypass techniques for forwarded traffic but allows to see client IP addresses in debug log
#POSTNAT=0

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

# mark bit used by nfqws to prevent loop
DESYNC_MARK=0x40000000
DESYNC_MARK_POSTNAT=0x20000000

TPWS_SOCKS_ENABLE=0
# tpws socks listens on this port on localhost and LAN interfaces
TPPORT_SOCKS=987
# use <HOSTLIST> and <HOSTLIST_NOAUTO> placeholders to engage standard hostlists and autohostlist in ipset dir
# hostlist markers are replaced to empty string if MODE_FILTER does not satisfy
# <HOSTLIST_NOAUTO> appends ipset/zapret-hosts-auto.txt as normal list
TPWS_SOCKS_OPT="
--filter-tcp=80 --methodeol <HOSTLIST> --new
--filter-tcp=443 --split-tls=sni --disorder <HOSTLIST>
"

TPWS_ENABLE=0
TPWS_PORTS=80,443
# use <HOSTLIST> and <HOSTLIST_NOAUTO> placeholders to engage standard hostlists and autohostlist in ipset dir
# hostlist markers are replaced to empty string if MODE_FILTER does not satisfy
# <HOSTLIST_NOAUTO> appends ipset/zapret-hosts-auto.txt as normal list
TPWS_OPT="
--filter-tcp=80 --methodeol <HOSTLIST> --new
--filter-tcp=443 --split-tls=sni --disorder <HOSTLIST>
"

NFQWS_ENABLE=1
# redirect outgoing traffic with connbytes limiter applied in both directions.
NFQWS_PORTS_TCP=80,443
NFQWS_PORTS_UDP=443
# PKT_OUT means connbytes dir original
# PKT_IN means connbytes dir reply
# this is --dpi-desync-cutoff=nX kernel mode implementation for linux. it saves a lot of CPU.
NFQWS_TCP_PKT_OUT=$((6+$AUTOHOSTLIST_RETRANS_THRESHOLD))
NFQWS_TCP_PKT_IN=3
NFQWS_UDP_PKT_OUT=$((6+$AUTOHOSTLIST_RETRANS_THRESHOLD))
NFQWS_UDP_PKT_IN=0
# redirect outgoing traffic without connbytes limiter and incoming with connbytes limiter
# normally it's needed only for stateless DPI that matches every packet in a single TCP session
# typical example are plain HTTP keep alives
# this mode can be very CPU consuming. enable with care !
#NFQWS_PORTS_TCP_KEEPALIVE=80
#NFQWS_PORTS_UDP_KEEPALIVE=
# use <HOSTLIST> and <HOSTLIST_NOAUTO> placeholders to engage standard hostlists and autohostlist in ipset dir
# hostlist markers are replaced to empty string if MODE_FILTER does not satisfy
# <HOSTLIST_NOAUTO> appends ipset/zapret-hosts-auto.txt as normal list
NFQWS_OPT="
--filter-tcp=80 --dpi-desync=fake,split2 --dpi-desync-fooling=md5sig <HOSTLIST> --new
--filter-tcp=443 --dpi-desync=fake,disorder2 --dpi-desync-ttl=0 --dpi-desync-ttl6=0 --dpi-desync-fooling=md5sig,badseq --dpi-desync-fake-tls=/opt/zapret/files/fake/tls_clienthello_www_google_com.bin --dpi-desync-repeats=20 <HOSTLIST> --new
--filter-udp=443 --dpi-desync=fake,disorder2 --dpi-desync-ttl=0 --dpi-desync-ttl6=0 --dpi-desync-fooling=md5sig,badseq --dpi-desync-fake-tls=/opt/zapret/files/fake/tls_clienthello_www_google_com.bin --dpi-desync-repeats=20 <HOSTLIST_NOAUTO>
"

# none,ipset,hostlist,autohostlist
MODE_FILTER=ipset,hostlist

# openwrt only : donttouch,none,software,hardware
FLOWOFFLOAD=donttouch

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
#IFACE_LAN=ethernet
#IFACE_WAN=eth1
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
#GETLIST=
```
{% endcode %}
{% endstep %}

{% step %}
При необходимости отредактируйте список адресов:

{% code overflow="wrap" %}
```bash
sudo nano /opt/zapret/ipset/zapret-hosts-user.txt
```
{% endcode %}
{% endstep %}

{% step %}
{% code title="zapret-hosts-user.txt" %}
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
{% endstep %}
{% endstepper %}

