---
description: 'Yay - менеджер пакетов AUR: Arch User Repository.'
---

# Пользовательский репозиторий AUR

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```
{% endcode %}
