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

#### mangohud

{% code overflow="wrap" %}
```bash
flatpak install org.freedesktop.Platform.VulkanLayer.MangoHud
```
{% endcode %}

Конфигурация:

{% tabs %}
{% tab title="mangohud.conf" %}
{% code overflow="wrap" %}
```bash
mkdir ~/.var/app/com.valvesoftware.Steam/config/MangoHud && nano ~/.var/app/com.valvesoftware.Steam/config/MangoHud/MangoHud.conf
```
{% endcode %}

Разрешите доступ к файлу конфигурации для `steam`:

{% code overflow="wrap" %}
```bash
flatpak override --user --filesystem=xdg-config/MangoHud:ro com.valvesoftware.Steam
```
{% endcode %}
{% endtab %}

{% tab title="→" %}
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

Включение `mangohud` во всех играх:

{% code overflow="wrap" %}
```bash
flatpak override --user --env=MANGOHUD=1 com.valvesoftware.Steam
```
{% endcode %}

#### gamescope

{% code overflow="wrap" %}
```bash
flatpak install org.freedesktop.Platform.VulkanLayer.gamescope
```
{% endcode %}

#### gamemode

Отредактируйте параметры запуска игры в `steam`, для включения `gamemode` режима:

{% code overflow="wrap" %}
```ini
gamemoderun %command%
```
{% endcode %}



### steam

{% code overflow="wrap" %}
```bash
flatpak install com.valvesoftware.Steam
```
{% endcode %}



### bottles

<figure><img src="../.gitbook/assets/bottles.png" alt=""><figcaption></figcaption></figure>

{% code overflow="wrap" %}
```bash
flatpak install com.usebottles.bottles
```
{% endcode %}



### lutris

{% code overflow="wrap" %}
```bash
flatpak install net.lutris.Lutris
```
{% endcode %}
