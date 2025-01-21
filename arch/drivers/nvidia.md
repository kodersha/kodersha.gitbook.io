---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# NVIDIA

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash"><a data-footnote-ref href="#user-content-fn-1">aura</a> -S --needed nvidia nvidia-utils lib32-nvidia-utils libvdpau lib32-libvdpau
</code></pre>



### NVIDIA beta

Для перехода на beta версию драйверов сначала удалите текущие. Узнать какие драйвера установлены можно командой:

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash"><a data-footnote-ref href="#user-content-fn-2">aura</a> -Qs nvidia
</code></pre>

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

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash"><a data-footnote-ref href="#user-content-fn-3">aura</a> -Rsu lib32-nvidia-utils nvidia-utils nvidia-dkms nvidia-settings steam
</code></pre>
{% endstep %}

{% step %}
Установите `beta` из AUR:

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash"><a data-footnote-ref href="#user-content-fn-4">aura</a> -A lib32-nvidia-utils-beta nvidia-utils-beta nvidia-beta nvidia-settings-beta
</code></pre>
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

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash"><a data-footnote-ref href="#user-content-fn-5">aura</a> -S steam
</code></pre>

[^1]: См. руководство по [aura](../repo/aura.md).

[^2]: См. руководство по [aura](../repo/aura.md).

[^3]: См. руководство по [aura](../repo/aura.md).

[^4]: См. руководство по [aura](../repo/aura.md).

[^5]: См. руководство по [aura](../repo/aura.md).
