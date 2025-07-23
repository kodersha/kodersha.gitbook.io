---
icon: box
---

# Репозитории

### RPMFusion

Репозиторий программного обеспечения для дистрибутивов Linux на основе RPM, таких как Fedora и RHEL. Он предоставляет пакеты, которые не включены в стандартные репозитории по различным причинам, например, из-за патентов, лицензий или других ограничений.

RPMFusion разделен на два репозитория: **`free`**, который содержит свободное программное обеспечение с открытым исходным кодом, и **`nonfree`**, где содержатся проприетарные программы или те, которые имеют ограничения по лицензии.

{% code overflow="wrap" %}
```bash
sudo rpm-ostree install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```
{% endcode %}

### homebrew

Менеджер пакетов, изначально разработанный для macOS, который позволяет легко устанавливать, обновлять и управлять программным обеспечением на linux-системах.

{% code overflow="wrap" %}
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
{% endcode %}

### flatpak

Позволяет устанавливать и запускать приложения в изолированных контейнерах, обеспечивая совместимость между дистрибутивами, автоматическое управление зависимостями и безопасное обновление через репозитории, такие как `flathub`.

Добавьте репозиторий `flathub`:

{% code overflow="wrap" %}
```bash
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
{% endcode %}
