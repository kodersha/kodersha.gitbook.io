---
icon: computer
---

# Драйвера

### Mesa и Vulkan

{% code overflow="wrap" %}
```bash
aura -S --needed mesa lib32-mesa vulkan-icd-loader lib32-vulkan-icd-loader
```
{% endcode %}



### Кодеки

{% code overflow="wrap" %}
```bash
aura -S --needed gst-libav gst-plugins-base gst-plugins-good gst-plugins-bad gst-plugins-ugly gstreamer-vaapi x265 x264 lame
```
{% endcode %}



### Аудио

{% code overflow="wrap" %}
```bash
aura -S --needed alsa-utils pipewire pipewire-pulse pipewire-jack wireplumber
```
{% endcode %}



### Bluetooth

{% code overflow="wrap" %}
```bash
aura -S --needed bluez bluez-utils
```
{% endcode %}

Включите сервис:

{% code overflow="wrap" %}
```bash
sudo systemctl enable --now bluetooth
```
{% endcode %}



### Интернет

{% code overflow="wrap" %}
```bash
aura -S --needed networkmanager networkmanager-openvpn networkmanager-pptp networkmanager-vpnc
```
{% endcode %}

Включите сервис:

{% code overflow="wrap" %}
```bash
sudo systemctl enable --now NetworkManager
```
{% endcode %}





***

{% code title="Одной командой" overflow="wrap" %}
```bash
aura -S --needed mesa lib32-mesa vulkan-icd-loader lib32-vulkan-icd-loader alsa-utils pipewire pipewire-pulse pipewire-jack wireplumber bluez bluez-utils networkmanager networkmanager-openvpn networkmanager-pptp networkmanager-vpnc gst-libav gst-plugins-base gst-plugins-good gst-plugins-bad gst-plugins-ugly gstreamer-vaapi x265 x264 lame
```
{% endcode %}





***

{% content-ref url="nvidia.md" %}
[nvidia.md](nvidia.md)
{% endcontent-ref %}

{% content-ref url="amd.md" %}
[amd.md](amd.md)
{% endcontent-ref %}
