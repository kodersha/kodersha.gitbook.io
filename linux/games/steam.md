# steam

{% code overflow="wrap" %}
```bash
sudo pacman -S steam
```
{% endcode %}

### Исправление ошибки 105

{% code overflow="wrap" %}
```bash
ln -sf ../run/systemd/resolve/stub-resolv.conf /etc/resolv.conf
```
{% endcode %}
