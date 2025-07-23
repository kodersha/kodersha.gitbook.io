---
description: >-
  Timeshift - утилита, которая служит для создания и управления резервными
  снимками (snapshots) файловой системы. Она позволяет восстанавливать систему
  до предыдущего состояния в случае сбоя или ошибки.
---

# Бэкапы

<figure><img src="../../.gitbook/assets/timeshift.png" alt=""><figcaption></figcaption></figure>

{% stepper %}
{% step %}
Установите `timeshift` и `cronie`:

{% code overflow="wrap" %}
```bash
aura -S timeshift cronie
```
{% endcode %}
{% endstep %}

{% step %}
Запустите сервис:

{% code overflow="wrap" %}
```bash
sudo systemctl enable --now cronie
```
{% endcode %}
{% endstep %}
{% endstepper %}



Настроить автоматическое создание снимков можно через GUI:

{% code overflow="wrap" %}
```bash
sudo timeshift-gtk
```
{% endcode %}



#### GRUB

Для добавления пункта меню с выбором снимков в `grub` -

{% stepper %}
{% step %}
Установите `grub-btrfs`:

{% code overflow="wrap" %}
```bash
aura -S grub-btrfs
```
{% endcode %}
{% endstep %}

{% step %}
Запустите сервис:

{% code overflow="wrap" %}
```bash
sudo systemctl enable --now grub-btrfsd
```
{% endcode %}
{% endstep %}

{% step %}
Обновите конфигурацию `grub`:

{% code overflow="wrap" %}
```bash
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
{% endcode %}
{% endstep %}
{% endstepper %}
