# Драйвера

### Mesa

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed mesa lib32-mesa
```
{% endcode %}



### Vulkan

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed vulkan-icd-loader lib32-vulkan-icd-loader
```
{% endcode %}



### NVIDIA

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed nvidia nvidia-utils lib32-nvidia-utils libvdpau lib32-libvdpau
```
{% endcode %}

<details>

<summary>NVIDIA beta</summary>

Для перехода на beta версию драйверов сначала удалите текущие. Узнать какие драйвера установлены можно командой:

{% code overflow="wrap" %}
```bash
pacman -Qs nvidia
```
{% endcode %}

{% code title="Пример" %}
```ini
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

_У вас могут быть другие драйвера, например `nvidia-open-dkms`._

Удалите найденные драйвера `nvidia`. Лучше всего в безопасной среде, например в консоли (Ctrl+Alt+F3). Также придётся удалить `steam` как зависимость.

{% code overflow="wrap" %}
```bash
sudo pacman -Rns lib32-nvidia-utils nvidia-utils nvidia-dkms nvidia-settings steam
```
{% endcode %}

Установите `beta` из AUR:

{% code overflow="wrap" %}
```bash
yay -S lib32-nvidia-utils-beta nvidia-utils-beta nvidia-beta nvidia-settings-beta
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

</details>



### Кодеки

{% code overflow="wrap" %}
```bash
yay -S --needed gst-libav gst-plugins-base gst-plugins-good gst-plugins-bad gst-plugins-ugly gstreamer-vaapi x265 x264 lame
```
{% endcode %}



### Аудио

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed alsa-utils pipewire pipewire-pulse pipewire-jack wireplumber
```
{% endcode %}



### Bluetooth

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed bluez bluez-utils
```
{% endcode %}

{% code title="Включите сервис" overflow="wrap" %}
```bash
sudo systemctl enable --now bluetooth
```
{% endcode %}



### Интернет

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed networkmanager networkmanager-openvpn networkmanager-pptp networkmanager-vpnc
```
{% endcode %}

{% code title="Включите сервис" overflow="wrap" %}
```bash
sudo systemctl enable --now NetworkManager
```
{% endcode %}



### Архивы

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed unzip zip unrar p7zip
```
{% endcode %}



***

{% code title="Одной командой" overflow="wrap" %}
```bash
sudo pacman -S --needed mesa lib32-mesa vulkan-icd-loader lib32-vulkan-icd-loader alsa-utils pipewire pipewire-pulse pipewire-jack wireplumber bluez bluez-utils networkmanager networkmanager-openvpn networkmanager-pptp networkmanager-vpnc unzip zip unrar p7zip
```
{% endcode %}

{% hint style="warning" %}
Драйвера `nvidia`  и кодеки не включены.
{% endhint %}
