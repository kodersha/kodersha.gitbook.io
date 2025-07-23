---
icon: gamepad-modern
---

# Игры

### Базовые библиотеки

{% code overflow="wrap" %}
```bash
aura -A wine-staging giflib lib32-giflib libpng lib32-libpng libldap lib32-libldap gnutls lib32-gnutls mpg123 lib32-mpg123 openal lib32-openal v4l-utils lib32-v4l-utils libpulse lib32-libpulse libgpg-error lib32-libgpg-error alsa-plugins lib32-alsa-plugins alsa-lib lib32-alsa-lib libjpeg-turbo lib32-libjpeg-turbo sqlite lib32-sqlite libxcomposite lib32-libxcomposite libxinerama lib32-libgcrypt libgcrypt lib32-libxinerama ncurses lib32-ncurses ocl-icd lib32-ocl-icd libxslt lib32-libxslt libva lib32-libva gtk3 lib32-gtk3 gst-plugins-base-libs lib32-gst-plugins-base-libs vulkan-icd-loader lib32-vulkan-icd-loader vkd3d lib32-vkd3d
```
{% endcode %}



### steam

{% tabs %}
{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install com.valvesoftware.Steam
```
{% endcode %}
{% endtab %}

{% tab title="pkg" %}
{% code overflow="wrap" %}
```bash
aura -S steam
```
{% endcode %}
{% endtab %}
{% endtabs %}



### mangohud

{% tabs %}
{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install org.freedesktop.Platform.VulkanLayer.MangoHud
```
{% endcode %}

Конфигурация:

{% code overflow="wrap" %}
```bash
mkdir ~/.var/app/com.valvesoftware.Steam/config/MangoHud && nano ~/.var/app/com.valvesoftware.Steam/config/MangoHud/MangoHud.conf
```
{% endcode %}

{% code title="mangohud.conf" %}
```ini
horizontal
legacy_layout=0
table_columns=20
fps
gpu_stats
gpu_temp
vram
cpu_stats
cpu_temp
ram
frametime=0
frame_timing=1
hud_no_margin
```
{% endcode %}

Разрешите доступ `mangohud` для `steam`:

{% code overflow="wrap" %}
```bash
flatpak override --user --filesystem=xdg-config/MangoHud:ro com.valvesoftware.Steam
```
{% endcode %}

Включите `mangohud` во всех играх, если нужно:

{% code overflow="wrap" %}
```bash
flatpak override --user --env=MANGOHUD=1 com.valvesoftware.Steam
```
{% endcode %}
{% endtab %}

{% tab title="pkg" %}
{% code overflow="wrap" %}
```bash
aura -S mangohud lib32-mangohud
```
{% endcode %}

Конфигурация:

{% code overflow="wrap" %}
```bash
mkdir ~/.config/MangoHud && nano ~/.config/MangoHud/MangoHud.conf
```
{% endcode %}

{% code title="mangohud.conf" %}
```ini
horizontal
legacy_layout=0
table_columns=20
fps
gpu_stats
gpu_temp
vram
cpu_stats
cpu_temp
ram
frametime=0
frame_timing=1
hud_no_margin
```
{% endcode %}
{% endtab %}
{% endtabs %}

Теперь можно включить `mangohud` в параметрах запуска игры в `steam`:

{% code overflow="wrap" %}
```bash
 mangohud %command%
```
{% endcode %}

Для использования с режимом `gamescope`:

{% code overflow="wrap" %}
```bash
gamescope --mangoapp -- %command%
```
{% endcode %}



### gamescope

{% tabs %}
{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install org.freedesktop.Platform.VulkanLayer.gamescope
```
{% endcode %}
{% endtab %}

{% tab title="pkg" %}
{% code overflow="wrap" %}
```bash
aura -S gamescope
```
{% endcode %}
{% endtab %}
{% endtabs %}



### gamemode

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



### bottles

<figure><img src="../.gitbook/assets/bottles.png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install com.usebottles.bottles
```
{% endcode %}
{% endtab %}

{% tab title="pkg" %}
{% code overflow="wrap" %}
```bash
aura -A bottles
```
{% endcode %}
{% endtab %}
{% endtabs %}



### lutris

{% tabs %}
{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install net.lutris.Lutris
```
{% endcode %}
{% endtab %}

{% tab title="pkg" %}
{% code overflow="wrap" %}
```bash
aura -S lutris
```
{% endcode %}
{% endtab %}
{% endtabs %}
