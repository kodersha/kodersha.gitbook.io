# NVIDIA

{% code overflow="wrap" %}
```bash
aura -S --needed nvidia nvidia-utils lib32-nvidia-utils libvdpau lib32-libvdpau
```
{% endcode %}



### NVIDIA beta

Для перехода на beta версию драйверов сначала удалите текущие. Узнать какие драйвера установлены можно командой:

{% code overflow="wrap" %}
```bash
aura -Qs nvidia
```
{% endcode %}

{% code title="Пример" %}
```bash
local/egl-wayland 2:1.1.13-2
    EGLStream-based Wayland external platform
local/lib32-nvidia-utils 550.90.07-1
    NVIDIA drivers utilities (32-bit)
local/libvdpau 1.5-2
    Nvidia VDPAU library
local/nvidia-dkms 550.90.07-2
    NVIDIA drivers - module sources
local/nvidia-utils 550.90.07-2
    NVIDIA drivers utilities
```
{% endcode %}

{% hint style="warning" %}
У вас могут быть другие драйвера, например `nvidia-open-dkms`.
{% endhint %}



{% stepper %}
{% step %}
Удалите найденные драйвера `nvidia`. Также придётся удалить `steam` как зависимость.

{% code overflow="wrap" %}
```bash
aura -Rsu lib32-nvidia-utils nvidia-utils nvidia-dkms nvidia-settings steam
```
{% endcode %}
{% endstep %}

{% step %}
Установите `beta` из AUR:

{% code overflow="wrap" %}
```bash
aura -A lib32-nvidia-utils-beta nvidia-utils-beta nvidia-beta nvidia-settings-beta
```
{% endcode %}
{% endstep %}

{% step %}
Перезагрузите систему:

{% code overflow="wrap" %}
```bash
sudo reboot
```
{% endcode %}
{% endstep %}
{% endstepper %}



Установите `steam` обратно, если нужно:

{% code overflow="wrap" %}
```bash
aura -S steam
```
{% endcode %}
