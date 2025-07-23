---
description: >-
  Утилита для работы с пакетами, которая предоставляет удобный интерфейс для
  управления как официальными пакетами из репозиториев Arch, так и
  пользовательскими пакетами из AUR.
---

# Aura

[Aura](https://github.com/fosskers/aura) позиционируется как продвинутая альтернатива `pacman`, с поддержкой дополнительных возможностей для работы с AUR.

{% hint style="info" %}
Пользовательский репозиторий [AUR](https://aur.archlinux.org/packages) (Arch User Repository) - поддерживаемое сообществом хранилище пакетов для пользователей Arch.
{% endhint %}

{% hint style="warning" %}
В дальнейшем руководстве по Arch linux я использую именно `aura` для установки и удаления тех или иных пакетов.
{% endhint %}



### Установка

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed base-devel git && git clone https://aur.archlinux.org/aura.git && cd aura && makepkg -s && sudo pacman -U aura-*.pkg.tar.zst && cd .. && rm -rf aura
```
{% endcode %}



{% content-ref url="../terminal/cmd.md" %}
[cmd.md](../terminal/cmd.md)
{% endcontent-ref %}
