# Оптимизация

{% hint style="danger" %}
Это не рекомендация к установке, система обычно и без этого работает хорошо «из коробки».
{% endhint %}

### cpupower

Используется для управления настройками процессора, включая выбор профиля энергопотребления (scaling governor).

{% code overflow="wrap" %}
```bash
sudo pacman -S cpupower
```
{% endcode %}

Основные планировщики (governors), которые можно использовать с `cpupower`:

* **performance**: Устанавливает частоту процессора на максимальный уровень для наилучшей производительности.
* **powersave**: Устанавливает частоту на минимальный уровень для минимального энергопотребления.
* **userspace**: Позволяет приложениям самостоятельно устанавливать частоты процессора.
* **ondemand**: Автоматически регулирует частоту процессора в зависимости от нагрузки. Быстро увеличивает частоту, когда это необходимо, и снижает её при уменьшении нагрузки.
* **conservative**: Похож на ondemand, но регулирует частоту плавнее. Полезно для уменьшения энергопотребления и нагрева.
* **schedutil**: Интегрирует регулирование частоты с планировщиком задач ядра и в реальном времени адаптирует частоту процессора в зависимости от текущей нагрузки.

Посмотреть доступные планировщики можно с помощью команды:

{% code overflow="wrap" %}
```sh
cpupower frequency-info
```
{% endcode %}

Для установки планировщика используйте команду `cpupower frequency-set`, например:

{% code overflow="wrap" %}
```sh
sudo cpupower frequency-set -g powersave
```
{% endcode %}

{% embed url="https://wiki.archlinux.org/title/CPU_frequency_scaling" %}

### zram

`zram` позволяет создать в оперативной памяти сжатый блок, который можно использовать как виртуальную память (swap). Основная идея заключается в том, что сжатие данных может позволить хранить больше данных в оперативной памяти, чем без сжатия.

{% embed url="https://wiki.archlinux.org/title/Zram" %}

Проще говоря, она сжимает данные, чтобы вместить больше информации в этот блок памяти. Это особенно полезно на устройствах с ограниченным количеством ОЗУ, поскольку позволяет использовать память эффективнее.

Стандартный `zswap` работает немного по-другому. Он добавляет уровень сжатия между оперативной памятью и дисковым swap. Когда системе нужно выгрузить данные из ОЗУ и записать их в swap, zswap сначала пытается сжать эти данные и хранить их в специальной области памяти. Если в этой области не хватает места, данные отправляются на диск (обычный swap).

{% hint style="info" %}
zram - создаёт сжатый блок памяти прямо в ОЗУ и использует его как swap.

zswap - добавляет прослойку сжатия между ОЗУ и обычным swap на диске, чтобы снизить нагрузку на диск и улучшить производительность.
{% endhint %}

Перед установкой `zram` нужно отключить `zswap`, для этого отредактируйте параметры ядра. Например в `grub`:

{% code overflow="wrap" %}
```bash
sudo nano /etc/default/grub
```
{% endcode %}

Найдите строку, начинающуюся с `GRUB_CMDLINE_LINUX_DEFAULT`, и добавьте параметр `zswap.enabled=0`.

{% code title="Пример" overflow="wrap" %}
```ini
GRUB_CMDLINE_LINUX_DEFAULT="quiet zswap.enabled=0"
```
{% endcode %}

Обновите конфигурацию `grub`:

{% code overflow="wrap" %}
```sh
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
{% endcode %}

Установите `zram-generator`:

{% code overflow="wrap" %}
```bash
sudo pacman -S zram-generator
```
{% endcode %}

Создайте файл конфигурации:

{% tabs %}
{% tab title="zram-generator.conf" %}
{% code overflow="wrap" %}
```bash
sudo nano /etc/systemd/zram-generator.conf
```
{% endcode %}
{% endtab %}

{% tab title="→" %}
```ini
[zram0]
zram-size = ram
compression-algorithm = zstd
swap-priority = 100
fs-type = swap
```

* **`zram-size = ram`**: Размер zram будет установлен равным объему доступной оперативной памяти (RAM). Таким образом, вся оперативная память может быть использована для zram.
* **`compression-algorithm = zstd`**: Указывает, какой алгоритм сжатия будет использоваться для сжатия данных в zram. В данном случае используется алгоритм `zstd`, который является одним из самых современных и эффективных алгоритмов сжатия.
* **`swap-priority = 100`**: Эта настройка задаёт приоритет использования zram по сравнению с другими swap-устройствами. Чем выше значение, тем приоритетнее устройство. Значение «100» указывает на высокий приоритет использования zram по сравнению с другими возможными swap-устройствами (например, swap-файлом на диске).
* **`fs-type = swap`**: Это указывает, что тип файловой системы, которая будет использоваться для zram — swap. То есть, zram будет использоваться как виртуальная память (swap-пространство).
{% endtab %}
{% endtabs %}

Запустите сервис:

{% code overflow="wrap" %}
```bash
sudo systemctl daemon-reload && sudo systemctl start systemd-zram-setup@zram0.service
```
{% endcode %}

### ananicy-cpp

Служба отслеживает активные процессы и назначает им приоритеты в соответствии с правилами.

{% embed url="https://gitlab.com/ananicy-cpp/ananicy-cpp" %}

Установите `ananicy-cpp`:

{% code overflow="wrap" %}
```bash
yay -S ananicy-cpp
```
{% endcode %}

Запустите сервис:

{% code overflow="wrap" %}
```bash
sudo systemctl enable --now ananicy-cpp
```
{% endcode %}

Дополнительно установите `cachyos-ananicy-rules-git`, набор правил с оптимизацией процессов от CachyOS:

{% code overflow="wrap" %}
```bash
yay -S cachyos-ananicy-rules-git
```
{% endcode %}

{% embed url="https://github.com/CachyOS/ananicy-rules" %}

### irqbalance

Сервис предназначен для управления распределением аппаратных прерываний (IRQ) между процессорными ядрами. Он автоматически распределяет IRQ так, чтобы снизить вероятность перегрузки одного ядра процессора, что может улучшить общую производительность системы.

{% code overflow="wrap" %}
```sh
sudo pacman -S irqbalance
```
{% endcode %}

Запустите сервис:

{% code overflow="wrap" %}
```sh
sudo systemctl enable --now irqbalance
```
{% endcode %}

{% embed url="https://github.com/Irqbalance/irqbalance" %}

### uksmd

Сервис служит для дедупликации страниц в памяти. Если есть несколько одинаковых страниц в оперативной памяти, они могут быть заменены одной общей страницей, что позволяет экономить и оптимизировать её использование.

{% embed url="https://github.com/CachyOS/uksmd" %}

{% hint style="warning" %}
Сервис работает только с ядром `linux-zen` или другим пропатченым ядром.
{% endhint %}

Установите:

{% code overflow="wrap" %}
```bash
yay -S uksmd
```
{% endcode %}

Запустите сервис:

{% code overflow="wrap" %}
```bash
sudo systemctl enable --now uksmd
```
{% endcode %}



### Оптимизированные пакеты

`ALHP` - репозиторий, аналогичный официальному репозиторию Arch, но его пакеты собраны для процессоров x86-64.

{% @github-files/github-code-block url="https://github.com/an0nfunc/ALHP" %}

`x86-64-v2`, `x86-64-v3` и `x86-64-v4` - разные группы дополнительных возможностей для 64-битных процессоров (Таких как Intel и AMD). Эти группы помогают разработчикам программного обеспечения понять, какие именно команды и возможности они могут использовать в своём программном обеспечении, чтобы оно работало наиболее эффективно на различных процессорах. Чем выше номер уровня, тем более новые и продвинутые команды могут поддерживать процессоры.

Определите какую версию поддерживает процессор:

```bash
/lib/ld-linux-x86-64.so.2 --help
```

{% hint style="danger" %}
Будьте внимательны, не добавляйте неподдерживаемые версии репозиториев, это сломает систему.
{% endhint %}

<pre data-title="Пример"><code>Subdirectories of glibc-hwcaps directories, in priority order:
  x86-64-v4
  x86-64-v3 <a data-footnote-ref href="#user-content-fn-1">(supported, searched)</a>
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

***

#### Источник:

{% embed url="https://ventureo.codeberg.page/" %}

[^1]: Значит, что для вашего процессора подойдёт v3.
