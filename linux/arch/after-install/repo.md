# Репозитории

### AUR

Пользовательский репозиторий AUR (Arch User Repository) - поддерживаемое сообществом хранилище программ для пользователей Arch.

{% embed url="https://aur.archlinux.org/packages" %}

#### aura

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed base-devel git && git clone https://aur.archlinux.org/aura.git && cd aura && makepkg -s
```
{% endcode %}

Установите пакет из папки aura. Название архива может отличаться от версии к версии.

{% code overflow="wrap" %}
```bash
sudo pacman -U aura-4.0.2-1-x86_64.pkg.tar.zst
```
{% endcode %}

#### pikaur

Ещё один установщик пакетов из AUR репозитория.

Установите `pikaur`:

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed base-devel git && git clone https://aur.archlinux.org/pikaur.git && cd pikaur && makepkg -fsri && cd .. && rm -rf pikaur
```
{% endcode %}

Теперь можно устанавливать ~~все игры~~ пакеты из AUR:

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash">pikaur -S <a data-footnote-ref href="#user-content-fn-1">pkg</a>
</code></pre>



### homebrew

[Homebrew](https://brew.sh/) для linux - это менеджер пакетов, изначально разработанный для macOS, который позволяет легко устанавливать, обновлять и управлять программным обеспечением на linux-системах.

{% code overflow="wrap" %}
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
{% endcode %}



### flatpak

Позволяет устанавливать и запускать приложения в изолированных контейнерах, обеспечивая совместимость между дистрибутивами, автоматическое управление зависимостями и безопасное обновление через репозитории, такие как `flathub`.

Установите `flatpak`:

{% code overflow="wrap" %}
```bash
aura -S flatpak
```
{% endcode %}

Добавьте репозиторий `flathub`:

{% code overflow="wrap" %}
```bash
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
{% endcode %}

{% embed url="https://flathub.org/" %}

[^1]: Название пакета AUR
