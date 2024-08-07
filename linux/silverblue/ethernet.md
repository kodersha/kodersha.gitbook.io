# 🔮 Интернет

### zapret

{% code overflow="wrap" %}
```bash
git clone --depth 1 https://github.com/bol-van/zapret && cd zapret
```
{% endcode %}

{% tabs %}
{% tab title="Установка" %}
{% code overflow="wrap" %}
```bash
./install_bin.sh
```
{% endcode %}

```bash
./install_prereq.sh
```

```bash
./blockcheck.sh
```

{% code overflow="wrap" %}
```bash
./install_easy.sh
```
{% endcode %}
{% endtab %}

{% tab title="→" %}
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
{% endtab %}
{% endtabs %}



{% code title="Отключите firewalld" overflow="wrap" %}
```bash
sudo systemctl disable firewalld
```
{% endcode %}

{% code title="Настройте службу" overflow="wrap" %}
```bash
sudo nano /etc/rc.d/rc.local
```
{% endcode %}

{% code title="rc.local" overflow="wrap" %}
```bash
#!/bin/bash

exec bash /opt/zapret/init.d/sysv/zapret start
```
{% endcode %}

{% code title="Права на выполнение" overflow="wrap" %}
```bash
sudo chmod 755 /etc/rc.d/rc.local
```
{% endcode %}

{% code title="Перезапустите службу" overflow="wrap" %}
```bash
sudo systemctl restart rc-local.service
```
{% endcode %}

{% code title="Создайте файл сервиса" overflow="wrap" %}
```bash
sudo nano /etc/systemd/system/rc-local.service
```
{% endcode %}

{% code title="rc-local.service" %}
```ini
[Unit]
Description=/etc/rc.d/rc.local Compatibility
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
{% endcode %}

{% code title="Перезапустите systemd" overflow="wrap" %}
```bash
sudo systemctl daemon-reload
```
{% endcode %}

{% code title="Запустите сервис" overflow="wrap" %}
```bash
sudo systemctl enable --now rc-local.service
```
{% endcode %}



{% code title="Отредактируйте конфигурацию nftables" overflow="wrap" %}
```bash
sudo nano /etc/nftables.conf
```
{% endcode %}

{% code title="nftables.conf" overflow="wrap" %}
```bash
table inet filter {
    chain output {
        type filter hook output priority 0; policy accept;

        # Блокировка исходящего трафика на порт UDP 443
        udp dport 443 drop
    }
}
```
{% endcode %}

{% code title="Примените конфигурацию" overflow="wrap" %}
```bash
sudo nft -f /etc/nftables.conf
```
{% endcode %}



{% code title="Дополнительный список url" overflow="wrap" %}
```bash
sudo nano /opt/zapret/ipset/zapret-hosts-user.txt
```
{% endcode %}

{% code title="zapret-hosts-user.txt" overflow="wrap" %}
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
