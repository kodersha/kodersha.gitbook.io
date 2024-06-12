# Драйвера

### Кодеки

{% code overflow="wrap" %}
```bash
yay -S gst-libav gst-plugins-base gst-plugins-good gst-plugins-bad gst-plugins-ugly gstreamer-vaapi x265 x264 lame
```
{% endcode %}

###

### NVIDIA beta

Для перехода на beta версию драйверов сначала удалите текущие. Узнать какие драйвера установлены можно командой:

{% code overflow="wrap" %}
```bash
pacman -Qs nvidia
```
{% endcode %}

{% code title="Пример" %}
```ini
local/egl-wayland 2:1.1.13-2.1
    EGLStream-based Wayland external platform
local/lib32-nvidia-utils 550.90.07-1
    NVIDIA drivers utilities (32-bit)
local/libvdpau 1.5-2.1
    Nvidia VDPAU library
local/nvidia-open-dkms 550.90.07-1
    NVIDIA open GPU kernel modules
local/nvidia-settings 550.90.07-1
    Tool for configuring the NVIDIA graphics driver
local/nvidia-utils 550.90.07-1
    NVIDIA drivers utilities
```
{% endcode %}

Удалите найденные драйвера `nvidia`. Лучше всего в безопасной среде, например в консоли (Ctrl+Alt+F3). Также придётся удалить `steam` как зависимость.

{% hint style="warning" %}
У вас могут быть другие драйвера, например `nvidia-dkms` или `nvidia`, а не `nvidia-open-dkms`.
{% endhint %}

{% code overflow="wrap" %}
```bash
sudo pacman -Rns lib32-nvidia-utils nvidia-utils nvidia-open-dkms nvidia-settings steam
```
{% endcode %}

Установите `beta` из AUR:

{% code overflow="wrap" %}
```bash
yay -S lib32-nvidia-utils-beta nvidia-utils-beta nvidia-open-beta-dkms nvidia-settings-beta
```
{% endcode %}

Установите `steam` обратно:

{% code overflow="wrap" %}
```bash
sudo pacman -S steam
```
{% endcode %}

Перезагрузите систему:

{% code overflow="wrap" %}
```bash
sudo reboot
```
{% endcode %}
