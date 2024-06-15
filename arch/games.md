---
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# 🎮 Игры

### Библиотеки

{% code overflow="wrap" %}
```bash
yay -S --needed wine-staging giflib lib32-giflib libpng lib32-libpng libldap lib32-libldap gnutls lib32-gnutls mpg123 lib32-mpg123 openal lib32-openal v4l-utils lib32-v4l-utils libpulse lib32-libpulse libgpg-error lib32-libgpg-error alsa-plugins lib32-alsa-plugins alsa-lib lib32-alsa-lib libjpeg-turbo lib32-libjpeg-turbo sqlite lib32-sqlite libxcomposite lib32-libxcomposite libxinerama lib32-libgcrypt libgcrypt lib32-libxinerama ncurses lib32-ncurses ocl-icd lib32-ocl-icd libxslt lib32-libxslt libva lib32-libva gtk3 lib32-gtk3 gst-plugins-base-libs lib32-gst-plugins-base-libs vulkan-icd-loader lib32-vulkan-icd-loader vkd3d lib32-vkd3d
```
{% endcode %}



### steam

{% code overflow="wrap" %}
```bash
sudo pacman -S steam
```
{% endcode %}

{% code title="mangohud" overflow="wrap" %}
```bash
sudo pacman -S mangohu
```
{% endcode %}

{% code title="gamescope" overflow="wrap" %}
```bash
sudo pacman -S gamescope
```
{% endcode %}

{% tabs %}
{% tab title="gamemode" %}
{% code overflow="wrap" %}
```bash
sudo pacman -S gamemode lib32-gamemode
```
{% endcode %}
{% endtab %}

{% tab title="→" %}
Отредактируйте параметры запуска игры в `steam`, для включения `gamemode` режима:

{% code overflow="wrap" %}
```ini
gamemoderun %command%
```
{% endcode %}
{% endtab %}
{% endtabs %}

***

{% code title="Одной командой:" overflow="wrap" %}
```bash
sudo pacman -S --needed mangohud gamescope gamemode lib32-gamemode steam
```
{% endcode %}



### bottles

{% code overflow="wrap" %}
```bash
yay -S bottles
```
{% endcode %}
