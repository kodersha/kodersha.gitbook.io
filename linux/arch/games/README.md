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

### Базовые библиотеки

{% code overflow="wrap" %}
```bash
aura -A --needed wine-staging giflib lib32-giflib libpng lib32-libpng libldap lib32-libldap gnutls lib32-gnutls mpg123 lib32-mpg123 openal lib32-openal v4l-utils lib32-v4l-utils libpulse lib32-libpulse libgpg-error lib32-libgpg-error alsa-plugins lib32-alsa-plugins alsa-lib lib32-alsa-lib libjpeg-turbo lib32-libjpeg-turbo sqlite lib32-sqlite libxcomposite lib32-libxcomposite libxinerama lib32-libgcrypt libgcrypt lib32-libxinerama ncurses lib32-ncurses ocl-icd lib32-ocl-icd libxslt lib32-libxslt libva lib32-libva gtk3 lib32-gtk3 gst-plugins-base-libs lib32-gst-plugins-base-libs vulkan-icd-loader lib32-vulkan-icd-loader vkd3d lib32-vkd3d
```
{% endcode %}

#### gamescope

{% tabs %}
{% tab title="pkg" %}
{% code overflow="wrap" %}
```bash
aura -S gamescope
```
{% endcode %}
{% endtab %}

{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install org.freedesktop.Platform.VulkanLayer.gamescope
```
{% endcode %}
{% endtab %}
{% endtabs %}

#### gamemode

{% code overflow="wrap" %}
```bash
aura -S gamemode lib32-gamemode
```
{% endcode %}

Отредактируйте параметры запуска игры в `steam`, для включения `gamemode` режима:

{% code overflow="wrap" %}
```ini
gamemoderun %command%
```
{% endcode %}

#### mangohud

{% tabs %}
{% tab title="pkg" %}
{% code overflow="wrap" %}
```bash
aura -S mangohud lib32-mangohud
```
{% endcode %}
{% endtab %}

{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install org.freedesktop.Platform.VulkanLayer.MangoHud
```
{% endcode %}
{% endtab %}
{% endtabs %}



### steam

{% tabs %}
{% tab title="pkg" %}
{% code overflow="wrap" %}
```bash
aura -S steam
```
{% endcode %}
{% endtab %}

{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install com.valvesoftware.Steam
```
{% endcode %}
{% endtab %}
{% endtabs %}



### bottles

{% tabs %}
{% tab title="pkg" %}
{% code overflow="wrap" %}
```bash
aura -A bottles
```
{% endcode %}
{% endtab %}

{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install com.usebottles.bottles
```
{% endcode %}
{% endtab %}
{% endtabs %}



### lutris

{% tabs %}
{% tab title="pkg" %}
{% code overflow="wrap" %}
```bash
aura -S lutris
```
{% endcode %}
{% endtab %}

{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install net.lutris.Lutris
```
{% endcode %}
{% endtab %}
{% endtabs %}
