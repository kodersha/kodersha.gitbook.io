---
description: >-
  Утилита для работы с пакетами, которая предоставляет удобный интерфейс для
  управления как официальными пакетами из репозиториев Arch, так и
  пользовательскими пакетами из AUR.
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



### Команды

* Управление пакетами из официальных репозиториев:
  * `aura -S <пакет>`: Установка пакета.
  * `aura -R <пакет>`: Удаление пакета.
  * `aura -Sy`: Синхронизация баз данных пакетов.
  * `aura -Syu`: Обновление системы.
* Работа с AUR:
  * `aura -A <пакет>`: Установка пакета из AUR.
  * `aura -Au`: Обновление всех пакетов, установленных из AUR.
  * `aura -Ap`: Предварительный просмотр пакетов из AUR перед их установкой.
* Журнал изменений и резервное копирование:
  * `aura -L`: Просмотр журнала установки и удаления пакетов.
  * `aura --restore`: Восстановление пакетов из резервной копии.
* Поиск пакетов:
  * `aura -As <ключевое слово>`: Поиск пакетов в официальных репозиториях.
  * `aura -Aa <ключевое слово>`: Поиск пакетов в AUR.





***

{% embed url="https://aur.archlinux.org/packages" %}
