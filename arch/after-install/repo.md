# Репозитории

### AUR

Пользовательский репозиторий AUR (Arch User Repository) - поддерживаемое сообществом хранилище программ для пользователей Arch.

{% embed url="https://aur.archlinux.org/packages" %}

#### yay

Установщик пакетов из AUR репозитория.

{% @github-files/github-code-block url="https://github.com/Jguer/yay" %}

Установите `yay`:

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -rsi && cd .. && rm -rf yay
```
{% endcode %}

Теперь можно устанавливать пакеты из AUR:

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash">yay -S <a data-footnote-ref href="#user-content-fn-1">pkg</a>
</code></pre>



### flatpak

Позволяет устанавливать и запускать приложения в изолированных контейнерах, обеспечивая совместимость между дистрибутивами, автоматическое управление зависимостями и безопасное обновление через репозитории, такие как `flathub`.

Установите `flatpak`:

{% code overflow="wrap" %}
```bash
sudo pacman -S flatpak
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
