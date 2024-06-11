# Драйвера

### NVIDIA beta

Для перехода на beta версию драйверов сначала удалите стандартные. Также придётся удалить Steam как зависимость.

{% code overflow="wrap" %}
```bash
sudo pacman -Rns lib32-nvidia-utils nvidia-open-dkms nvidia-settings nvidia-utils steam
```
{% endcode %}

Установите `beta` из AUR:

{% code overflow="wrap" %}
```bash
yay -S lib32-nvidia-utils-beta nvidia-open-beta-dkms nvidia-settings-beta nvidia-utils-beta
```
{% endcode %}

Установите `steam` обратно:

```bash
sudo pacman -S steam
```
