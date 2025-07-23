---
icon: gamepad-modern
---

# Игры

### steam

{% code overflow="wrap" %}
```bash
flatpak install com.valvesoftware.Steam
```
{% endcode %}

### protontricks

{% code overflow="wrap" %}
```bash
flatpak install com.github.Matoking.protontricks
```
{% endcode %}

### gamescope

{% code overflow="wrap" %}
```bash
flatpak install org.freedesktop.Platform.VulkanLayer.gamescope
```
{% endcode %}

### proton-ge

{% code overflow="wrap" %}
```bash
flatpak install com.valvesoftware.Steam.CompatibilityTool.Proton-GE
```
{% endcode %}

### vkbasalt

{% code overflow="wrap" %}
```bash
flatpak install org.freedesktop.Platform.VulkanLayer.vkBasalt
```
{% endcode %}

### gamemode

{% code title="Параметр запуска игры в steam, для включения gamemode режима:" overflow="wrap" %}
```ini
gamemoderun %command%
```
{% endcode %}

### mangohud

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

{% code title="Разрешите доступ к файлу конфигурации:" overflow="wrap" %}
```bash
flatpak override --user --filesystem=xdg-config/MangoHud:ro com.valvesoftware.Steam
```
{% endcode %}

***

Для [`bottles`](games.md#bottles):

{% code overflow="wrap" %}
```bash
mkdir ~/.var/app/com.usebottles.bottles/config/MangoHud && nano ~/.var/app/com.usebottles.bottles/config/MangoHud/MangoHud.conf
```
{% endcode %}

{% code title="Разрешите доступ к файлу конфигурации:" overflow="wrap" %}
```bash
flatpak override --user --filesystem=xdg-config/MangoHud:ro com.usebottles.bottles
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

{% code title="Для использования с режимом gamescope:" overflow="wrap" %}
```bash
gamescope --mangoapp -- %command%
```
{% endcode %}

{% code title="Включение mangohud во всех играх:" overflow="wrap" %}
```bash
flatpak override --user --env=MANGOHUD=1 com.valvesoftware.Steam
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
