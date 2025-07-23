# Оптимизация

{% hint style="danger" %}
Это не рекомендация к установке, система обычно и без этого работает хорошо «из коробки».
{% endhint %}

### cpupower

Используется для управления настройками процессора, включая выбор профиля энергопотребления (scaling governor).

{% code overflow="wrap" %}
```bash
aura -S cpupower
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
aura -S zram-generator
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

{% code title="Запустите сервис" overflow="wrap" %}
```bash
sudo systemctl daemon-reload && sudo systemctl start systemd-zram-setup@zram0.service
```
{% endcode %}



### ananicy-cpp

Служба отслеживает активные процессы и назначает им приоритеты в соответствии с правилами.

{% embed url="https://gitlab.com/ananicy-cpp/ananicy-cpp" %}

{% code title="Установите ananicy-cpp" overflow="wrap" %}
```bash
aura -A ananicy-cpp
```
{% endcode %}

{% code title="Запустите сервис" overflow="wrap" %}
```bash
sudo systemctl enable --now ananicy-cpp
```
{% endcode %}

Дополнительно установите `cachyos-ananicy-rules-git`, набор правил с оптимизацией процессов от CachyOS:

{% code overflow="wrap" %}
```bash
aura -A cachyos-ananicy-rules-git
```
{% endcode %}

{% embed url="https://github.com/CachyOS/ananicy-rules" %}



### irqbalance

Сервис предназначен для управления распределением аппаратных прерываний (IRQ) между процессорными ядрами. Он автоматически распределяет IRQ так, чтобы снизить вероятность перегрузки одного ядра процессора, что может улучшить общую производительность системы.

{% code overflow="wrap" %}
```sh
aura -S irqbalance
```
{% endcode %}

{% code title="Запустите сервис" overflow="wrap" %}
```sh
sudo systemctl enable --now irqbalance
```
{% endcode %}

{% embed url="https://github.com/Irqbalance/irqbalance" %}



### uksmd

{% hint style="danger" %}
Сервис работает только с ядром `linux-zen` или другим пропатченым ядром.
{% endhint %}

Сервис служит для дедупликации страниц в памяти. Если есть несколько одинаковых страниц в оперативной памяти, они могут быть заменены одной общей страницей, что позволяет экономить и оптимизировать её использование.

{% embed url="https://github.com/CachyOS/uksmd" %}

{% code title="Установите" overflow="wrap" %}
```bash
aura -A uksmd
```
{% endcode %}

{% code title="Запустите сервис" overflow="wrap" %}
```bash
sudo systemctl enable --now uksmd
```
{% endcode %}

***

#### Источник:

{% embed url="https://ventureo.codeberg.page/" %}
