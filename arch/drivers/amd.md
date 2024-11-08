---
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: false
  pagination:
    visible: false
---

# AMD

{% code overflow="wrap" %}
```bash
aura -S --needed libva-mesa-driver lib32-libva-mesa-driver mesa-vdpau lib32-mesa-vdpau libva-vdpau-driver lib32-libva-vdpau-driver vulkan-radeon lib32-vulkan-radeon
```
{% endcode %}

Некоторые системы требуют раннего запуска KMS (Kernel Mode Setting) для корректной работы.

{% code overflow="wrap" %}
```bash
sudo nano /etc/mkinitcpio.conf
```
{% endcode %}

Добавьте `amdgpu` к `MODULES=()`.

{% code overflow="wrap" %}
```ini
MODULES=(amdgpu)
```
{% endcode %}

И выполните:

{% code overflow="wrap" %}
```bash
sudo mkinitcpio -P
```
{% endcode %}

### CoreCtrl

<figure><img src="../../linux/.gitbook/assets/corectl.png" alt=""><figcaption></figcaption></figure>

{% code overflow="wrap" %}
```bash
aura -S corectrl
```
{% endcode %}
