# Оптимизация

### cpupower

В Arch Linux утилита `cpupower` используется для управления настройками процессора, включая выбор профиля энергопотребления (scaling governor).&#x20;

{% code overflow="wrap" %}
```bash
sudo pacman -S cpupower
```
{% endcode %}

Основные планировщики (governors), которые можно использовать с `cpupower`:

1. **performance**: Устанавливает частоту процессора на максимальный уровень для наилучшей производительности.
2. **powersave**: Устанавливает частоту на минимальный уровень для минимального энергопотребления.
3. **userspace**: Позволяет приложениям самостоятельно устанавливать частоты процессора.
4. **ondemand**: Автоматически регулирует частоту процессора в зависимости от нагрузки. Быстро увеличивает частоту, когда это необходимо, и снижает её при уменьшении нагрузки.
5. **conservative**: Похож на ondemand, но регулирует частоту плавнее. Полезно для уменьшения энергопотребления и нагрева.
6. **schedutil**: Интегрирует регулирование частоты с планировщиком задач ядра и в реальном времени адаптирует частоту процессора в зависимости от текущей нагрузки.

Для установки планировщика используйте команду `cpupower frequency-set`, например:

```sh
sudo cpupower frequency-set -g performance
```

Также можно просматривать доступные планировщики с помощью команды:

```sh
cpupower frequency-info
```



Например я использую планировщик `conservative` с настройками для плавного увеличения и уменьшения частоты процессора.

```bash
sudo cpupower frequency-set -g conservative
```

Дополнительно можно создать файл systemd-сервиса для автоматической настройки нужного планировщика при загрузке системы:

{% tabs %}
{% tab title="cpupower.service" %}
{% code overflow="wrap" %}
```bash
sudo nano /etc/systemd/system/cpupower.service
```
{% endcode %}
{% endtab %}

{% tab title="→" %}
```editorconfig
[Unit]
Description=Set CPU power governor to conservative
After=multi-user.target

[Service]
Type=oneshot
ExecStart=/usr/bin/cpupower frequency-set -g conservative
ExecStart=/bin/bash -c 'echo "35" > /sys/devices/system/cpu/cpufreq/conservative/up_threshold'
ExecStart=/bin/bash -c 'echo "20" > /sys/devices/system/cpu/cpufreq/conservative/down_threshold'
ExecStart=/bin/bash -c 'echo "5" > /sys/devices/system/cpu/cpufreq/conservative/freq_step'
ExecStart=/bin/bash -c 'echo "5" > /sys/devices/system/cpu/cpufreq/conservative/sampling_down_factor'

[Install]
WantedBy=multi-user.target
```
{% endtab %}
{% endtabs %}

Включите сервис:

{% code overflow="wrap" %}
```bash
sudo systemctl enable --now cpupower.service
```
{% endcode %}
