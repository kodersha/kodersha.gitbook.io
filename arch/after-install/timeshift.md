---
description: >-
  Timeshift - утилита, которая служит для создания и управления резервными
  снимками (snapshots) файловой системы. Она позволяет восстанавливать систему
  до предыдущего состояния в случае сбоя или ошибки.
---

# Бэкапы

<figure><img src="../.gitbook/assets/timeshift.png" alt=""><figcaption></figcaption></figure>

Установите `timeshift` и `cronie`:

{% code overflow="wrap" %}
```bash
yay -S timeshift cronie
```
{% endcode %}

Запустите сервис:

{% code overflow="wrap" %}
```bash
sudo systemctl enable --now cronie
```
{% endcode %}

***

Настроить автоматическое создание снимков можно через GUI:

{% code overflow="wrap" %}
```bash
sudo timeshift-gtk
```
{% endcode %}



### GRUB

Для добавления пункта меню с выбором снимков в `grub` установите `grub-btrfs`:

{% code overflow="wrap" %}
```bash
sudo pacman -S grub-btrfs
```
{% endcode %}

Запустите сервис:

{% code overflow="wrap" %}
```bash
sudo systemctl enable --now grub-btrfsd
```
{% endcode %}

Обновите конфигурацию `grub`:

{% code overflow="wrap" %}
```bash
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
{% endcode %}
