# Репозитории

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

`flatpak` позволяет устанавливать и запускать приложения в изолированных контейнерах, обеспечивая совместимость между дистрибутивами, автоматическое управление зависимостями и безопасное обновление через репозитории, такие как `flathub`.

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



### Оптимизированные пакеты

Репозиторий, аналогичный официальному репозиторию Arch, но его пакеты собраны для процессоров x86-64.

{% embed url="https://github.com/an0nfunc/ALHP" %}

`x86-64-v2`, `x86-64-v3` и `x86-64-v4` - это разные группы дополнительных возможностей для современных 64-битных процессоров (Таких как Intel и AMD). Эти группы помогают разработчикам программного обеспечения понять, какие именно команды и возможности они могут использовать в своём программном обеспечении, чтобы оно работало наиболее эффективно на различных процессорах. Чем выше номер уровня (v2, v3, v4), тем более новые и продвинутые команды могут поддерживать процессоры.

Определите какую версию поддерживает процессор:

```bash
/lib/ld-linux-x86-64.so.2 --help
```

{% hint style="danger" %}
Будьте внимательны, не добавляйте неподдерживаемые весрии репозиториев, это сломает систему.
{% endhint %}

<pre data-title="Пример"><code>Subdirectories of glibc-hwcaps directories, in priority order:
  x86-64-v4
  x86-64-v3 <a data-footnote-ref href="#user-content-fn-2">(supported, searched)</a>
  x86-64-v2 (supported, searched)
</code></pre>

Например процессор поддерживает `v2` и `v3` (supported, searched), значит можно использовать репозиторий `v3`.

Установите ключи и mirrorlist:

{% code overflow="wrap" %}
```bash
yay -S alhp-keyring alhp-mirrorlist
```
{% endcode %}

Отредактируйте конфигурацию pacman:

{% tabs %}
{% tab title="pacman.conf" %}
{% code overflow="wrap" %}
```bash
sudo nano /etc/pacman.conf
```
{% endcode %}
{% endtab %}

{% tab title="→" %}
Добавьте репозитории в конфигурацию:

{% code title="Например для v3" %}
```ini
[core-x86-64-v3]
Include = /etc/pacman.d/alhp-mirrorlist

[extra-x86-64-v3]
Include = /etc/pacman.d/alhp-mirrorlist

[core]
Include = /etc/pacman.d/mirrorlist

[extra]
Include = /etc/pacman.d/mirrorlist

# if you need [multilib] support
[multilib-x86-64-v3]
Include = /etc/pacman.d/alhp-mirrorlist

[multilib]
Include = /etc/pacman.d/mirrorlist
```
{% endcode %}
{% endtab %}
{% endtabs %}

Обновите систему:

```bash
sudo pacman -Syyuu
```

[^1]: Название пакета AUR

[^2]: Значит, что для вашего процессора подойдёт v3.
