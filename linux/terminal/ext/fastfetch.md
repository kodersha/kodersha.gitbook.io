# fastfetch

<figure><img src="../../../.gitbook/assets/fetch.png" alt=""><figcaption></figcaption></figure>

{% code overflow="wrap" %}
```bash
sudo pacman -S fastfetch
```
{% endcode %}

***

Создайте файл пользовательской конфигурации:

{% code overflow="wrap" %}
```bash
fastfetch --gen-config-force
```
{% endcode %}

{% tabs %}
{% tab title="config.jsonc" %}
```bash
nano ~/.config/fastfetch/config.jsonc
```

```json
{
  "$schema": "https://github.com/fastfetch-cli/fastfetch/raw/dev/doc/json_schema.json",
  "logo": {
    "source": "~/.config/fastfetch/logo.txt",
    "color": {
      "1": "blue"
    },
    "padding": {
      "top": 2,
      "left": 1
    }
  },
  "display": {
    "separator": "· ",
    "color": "blue"
  },
  "modules": [{
      "type": "title",
      "keyColor": "blue",
      "format": "{6}{7}{8}"
    },
    "break",
    {
      "key": "OS         ",
      "keyColor": "blue",
      "type": "os"
    },
    {
      "key": "Kernel     ",
      "keyColor": "blue",
      "type": "kernel",
      "format": "{1} {2}"
    },
    {
      "key": "Packages   ",
      "keyColor": "blue",
      "type": "packages"
    },
    {
      "key": "Processes  ",
      "keyColor": "blue",
      "type": "processes"
    },
    "break",
    {
      "key": "WM         ",
      "keyColor": "blue",
      "type": "wm"
    },
    {
      "key": "DE         ",
      "keyColor": "blue",
      "type": "de"
    },
    "break",
    {
      "key": "Shell      ",
      "keyColor": "blue",
      "type": "shell"
    },
    {
      "key": "Terminal   ",
      "keyColor": "blue",
      "type": "terminal"
    },
    "break",
    {
      "key": "Board      ",
      "keyColor": "blue",
      "type": "board"
    },
    {
      "key": "BIOS       ",
      "keyColor": "blue",
      "type": "bios"
    },
    "break",
    {
      "key": "CPU        ",
      "keyColor": "blue",
      "type": "cpu"
    },
    {
      "key": "GPU        ",
      "keyColor": "blue",
      "type": "gpu",
      "format": "{1} {2} ({3})"
    },
    "break",
    {
      "key": "Memory     ",
      "keyColor": "blue",
      "type": "memory"
    },
    {
      "key": "Swap       ",
      "keyColor": "blue",
      "type": "swap"
    },
    "break",
    {
      "key": "Disk       ",
      "keyColor": "blue",
      "type": "disk"
    },
    "break",
    {
      "key": "Monitor    ",
      "keyColor": "blue",
      "type": "monitor",
      "format": "{1}"
    },
    {
      "key": "Resolution ",
      "keyColor": "blue",
      "type": "display",
      "compactType": "original-with-refresh-rate"
    },
    "break",
    {
      "key": "Uptime     ",
      "keyColor": "blue",
      "type": "uptime"
    },
    "break",
    {
      "type": "colors",
      "symbol": "circle"
    }
  ]
}
```
{% endtab %}

{% tab title="logo.txt" %}
{% code overflow="wrap" %}
```bash
nano ~/.config/fastfetch/logo.txt
```
{% endcode %}

```asciidoc
⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡿⠿⠿⠟⣛⢛⠻⠿⠿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⠿⠛⠋⠉⠉⣡⣴⡞⣿⣿⣿⡟⢿⣿⣶⣦⣍⡛⠿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⡿⠋⡡⠶⢋⡾⢁⣾⣿⣿⡇⢹⣿⣿⣿⣶⣌⠙⢿⣿⣷⣴⣌⠛⢿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⡿⢋⡠⢀⣴⣷⣿⠃⣾⣿⣿⣿⣷⡌⢿⣿⣿⣿⣿⣿⣦⡉⠻⣿⣿⣿⣦⠙⢿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⠟⣠⡻⢡⣿⣿⣿⡗⢰⣿⣿⣿⣿⣿⣷⡈⣿⣿⣿⣿⣿⣿⣿⣦⡙⢿⣿⣽⣷⡌⢻⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⠟⣀⡿⢡⣿⣿⣿⣿⡄⢸⣿⣿⣿⠿⠿⡿⢷⠸⣿⣿⣿⣿⣿⣿⣿⣿⣌⢻⣿⣿⣿⡄⢿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⡟⣠⣿⠁⣿⣿⣿⣯⣍⠃⢸⡿⣿⠁⢰⡆⠈⢿⡆⢻⣿⣿⣿⣿⣿⣿⣿⣿⣆⢹⣿⣿⣿⡈⢿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⠁⣿⡇⣸⣿⡿⠿⠿⠟⣀⣀⣁⣈⡁⢸⡇⢠⣴⣤⣴⣶⣶⣦⣬⣭⣍⣉⣙⠃⡂⢻⣿⣿⣧⠸⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⠃⣴⣿⠀⣤⣴⣾⣿⣿⣿⣿⣿⣿⣿⣿⣤⣤⣼⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡀⣟⡀⢿⣿⣿⡄⢿⣿⣿⣿⣿⣿⣿⣿
⣿⡿⠀⣿⡟⠀⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡇⣿⣷⢈⡻⣿⡇⠸⣿⣿⣿⣿⣿⣿⣿
⣿⡇⣾⣇⡆⡆⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡇⠉⣿⡆⢿⣿⣷⠀⣿⣿⣿⣿⣿⣿⣿
⣿⠃⣿⣿⠀⠂⢹⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣗⠀⡙⢣⡈⣻⣿⠀⢻⣿⣿⣿⣿⣿⣿
⡿⢰⣿⣿⠀⡅⢸⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣷⢀⣿⣿⣿⣿⣿⡄⢸⣿⣿⣿⣿⣿⣿
⡇⢸⣿⣿⠀⡃⢸⣿⣿⣿⣿⣿⡿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⢿⣿⣿⣿⣿⣿⣿⣿⠸⣿⣿⣿⣿⣿⡇⢸⣿⣿⣿⣿⣿⣿
⠁⠀⣿⢿⡆⠃⢸⣿⣿⣿⣿⣿⠀⠀⣹⣿⣿⣯⣭⣭⣭⣿⣿⡃⠀⢈⣿⣿⣿⣿⣿⣿⢸⣿⣿⣿⣿⣿⡇⢸⣿⣿⣿⣿⣿⣿
⠀⠀⠻⡜⣇⠀⢸⣿⣿⣿⣿⣿⣷⣾⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣶⣾⣿⣿⣿⣿⣿⣿⢸⣿⣷⡌⣿⣿⡇⢸⣿⣿⣿⣿⣿⣿
⠀⢸⠰⢻⠘⡅⠸⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⢸⣿⣿⡇⣿⣿⠇⢸⣿⣿⣿⣿⣿⣿
⠀⠀⠀⢼⣷⣷⠀⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⢸⡏⣿⡇⣿⣿⠁⢸⣿⣿⣿⣿⣿⣿
⡆⠘⡄⢹⣿⣿⡄⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⢸⡇⣿⡇⣿⣿⡇⢸⣿⣿⣿⣿⣿⣿
⡇⠀⡇⢸⡟⠿⣄⢸⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⢸⢀⣿⡇⣿⣿⡅⠈⣿⣿⣿⣿⣿⣿
⣷⠀⠹⢸⣿⡆⣿⢸⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⠘⢸⣿⡇⣿⣿⡇⡇⣿⣿⣿⣿⣿⣿
⣿⣇⠀⠘⣿⠁⢠⢈⡛⠛⠛⣋⠉⠉⠉⣉⠉⠉⠩⠍⣭⡭⠭⠉⠉⠈⠁⣭⠉⡍⣭⣍⠀⣸⣿⡇⣿⣻⠁⡇⣿⣿⣿⣿⣿⣿
⣿⣿⣆⠀⢻⡇⢸⡆⢻⣿⡆⣿⡇⢿⡁⣿⡇⠀⠀⠀⠀⠀⠀⠀⠀⢀⡄⣿⠀⡇⢻⣿⢡⣿⣿⡇⡿⢻⠀⡅⢹⣿⣿⣿⣿⣿
⣿⣿⣿⣦⠀⣿⢸⣯⠸⣿⡇⣿⣷⠸⡇⠸⠓⠀⠀⠆⠀⠀⠀⠀⣠⣿⡇⠛⠰⡇⣹⡟⢸⣿⣿⡇⣿⣾⡐⡇⠈⣿⣿⣿⣿⣿
⣿⣿⣿⣿⠀⢹⠘⣿⣆⢻⣧⢸⣿⠀⠀⠀⠀⢠⡀⠀⠀⣀⣠⣾⣿⣿⣇⠀⠀⠀⠿⠁⣿⣿⣿⣇⣿⣿⣇⢩⡆⢿⣿⣿⣿⣿
⣿⣿⣿⣿⡄⣿⠀⣿⣿⡘⡟⠘⠃⠀⠀⠀⣤⣼⣿⣿⣿⣿⣿⣿⣿⣿⣿⣶⡆⠀⡆⠀⠉⠉⠛⠿⢿⣿⣿⡄⣧⢸⣿⣿⣿⣿
⣿⣿⣿⣿⡇⣿⠆⠟⠋⠁⠁⠀⠀⠀⠀⠀⠸⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡟⠀⢀⠇⠀⠀⠀⠀⠀⠀⠀⠉⠁⠛⠈⣿⣿⣿⣿
⣿⣿⠿⠟⣁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠸⣿⡿⠿⠿⠛⠻⠿⣿⣿⠁⠀⠈⠀⠀⠀⠀⣀⡀⠀⠀⠀⠀⠂⠀⠀⠈⠛⢿
⠋⠀⠀⠀⠈⠉⠛⠛⠳⠦⠤⢄⣀⠀⠀⠀⠀⠀⢠⡤⠴⠶⠾⠷⢤⢀⠁⠀⠀⠀⠀⣠⠴⠋⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸
```
{% endtab %}
{% endtabs %}
