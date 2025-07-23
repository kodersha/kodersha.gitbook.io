# AMD

{% code overflow="wrap" %}
```bash
aura -S --needed libva-mesa-driver lib32-libva-mesa-driver mesa-vdpau lib32-mesa-vdpau libva-vdpau-driver lib32-libva-vdpau-driver vulkan-radeon lib32-vulkan-radeon
```
{% endcode %}



Некоторые системы требуют раннего запуска KMS (Kernel Mode Setting) для корректной работы.

{% stepper %}
{% step %}
{% code overflow="wrap" %}
```bash
sudo nano /etc/mkinitcpio.conf
```
{% endcode %}
{% endstep %}

{% step %}
Добавьте `amdgpu` к `MODULES=()`:

{% code overflow="wrap" %}
```ini
MODULES=(amdgpu)
```
{% endcode %}
{% endstep %}

{% step %}
И выполните:

{% code overflow="wrap" %}
```bash
sudo mkinitcpio -P
```
{% endcode %}
{% endstep %}
{% endstepper %}



### CoreCtrl

<figure><img src="../../.gitbook/assets/corectl.png" alt=""><figcaption></figcaption></figure>

{% code overflow="wrap" %}
```bash
aura -S corectrl
```
{% endcode %}
