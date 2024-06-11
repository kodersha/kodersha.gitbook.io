# Пользовательский репозиторий

Пользовательский репозиторий AUR (Arch User Repository) - поддерживаемое сообществом хранилище программ для пользователей Arch.

{% embed url="https://aur.archlinux.org/packages" %}



### yay

Помощник для управления пакетами в Arch Linux, упрощает установку и управление пакетами из AUR.

{% embed url="https://github.com/Jguer/yay" %}

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

`flatpak` позволяет устанавливать и запускать приложения в изолированных контейнерах, обеспечивая совместимость между дистрибутивами, автоматическое управление зависимостями и безопасное обновление через репозитории, такие как flathub.

{% embed url="https://flatpak.org/" %}

Установите `flatpak`:

{% code overflow="wrap" %}
```bash
sudo pacman -S flatpak
```
{% endcode %}



`flathub` - репозиторий приложений `flatpak`.

{% embed url="https://flathub.org/" %}

Добавьте репозиторий `flathub` для `system`:

{% code overflow="wrap" %}
```bash
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
{% endcode %}

И для `user`:

{% code overflow="wrap" %}
```bash
flatpak remote-add --user --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
{% endcode %}

[^1]: Название пакета AUR
