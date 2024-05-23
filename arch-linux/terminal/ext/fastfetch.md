# fastfetch



{% tabs %}
{% tab title="fedora" %}
sudo dnf install fastfetch
{% endtab %}

{% tab title="arch" %}
sudo pacman -S fastfetch
{% endtab %}
{% endtabs %}

{% code overflow="wrap" %}
```bash
fastfecth --gen-config-force
```
{% endcode %}

```bash
nano ~/.config/fastfetch/config.jsonc
```

***

{% code title="config.jsonc" %}
```json
{
    "$schema": "https://github.com/fastfetch-cli/fastfetch/raw/dev/doc/json_schema.json",
    "logo": {
        "source": "~/.config/fastfetch/logo.txt"
    },
    "display": {
        "separator": "·   "
    },
    "modules": [{
            "type": "title",
            "keyColor": "blue",
            "format": "      {6}{7}{8}"
        },
        "break",
        {
            "type": "custom",
            "format": "┌───────────────────────────── \u001b[1mSystem Information\u001b[0m ─────────────────────────────┐" // `\u001b` is `\033`, or `\e`
        },
        "break",
        {
            "key": "      OS           ",
            "keyColor": "blue",
            "type": "os"
        },
        {
            "key": "      Kernel       ",
            "keyColor": "blue",
            "type": "kernel"
        },
        {
            "key": "      Packages     ",
            "keyColor": "blue",
            "type": "packages"
        },
        {
            "key": "      Processes    ",
            "keyColor": "blue",
            "type": "processes"
        },
        "break",
        {
            "key": "      WM           ",
            "keyColor": "blue",
            "type": "wm"
        },
        {
            "key": "      DE           ",
            "keyColor": "blue",
            "type": "de"
        },
        "break",
        {
            "key": "      Shell        ",
            "keyColor": "blue",
            "type": "shell"
        },
        {
            "key": "      Terminal     ",
            "keyColor": "blue",
            "type": "terminal"
        },
        "break",
        {
            "key": "      Board        ",
            "keyColor": "blue",
            "type": "board"
        },
        {
            "key": "      BIOS         ",
            "keyColor": "blue",
            "type": "bios"
        },
        "break",
        {
            "key": "      CPU          ",
            "keyColor": "blue",
            "type": "cpu"
        },
        {
            "key": "      GPU          ",
            "keyColor": "blue",
            "type": "gpu"
        },
        "break",
        {
            "key": "      Memory       ",
            "keyColor": "blue",
            "type": "memory"
        },
        {
            "key": "      Swap         ",
            "keyColor": "blue",
            "type": "swap"
        },
        "break",
        {
            "key": "      SSD          ",
            "keyColor": "blue",
            "type": "disk"
        },
        "break",
        {
            "key": "      Monitor      ",
            "keyColor": "blue",
            "type": "monitor",
            "format": "{1}"
        },
        {
            "key": "      Resolution   ",
            "keyColor": "blue",
            "type": "display",
            "compactType": "original-with-refresh-rate"
        },
        "break",
        {
            "key": "      Uptime       ",
            "keyColor": "blue",
            "type": "uptime"
        },
        "break",
        {
            "type": "custom",
            "format": "└──────────────────────────────────────────────────────────────────────────────┘" // `\u001b` is `\033`, or `\e`
        },
        "break",
        {
            "type": "colors",
            "paddingLeft": 6,
            "symbol": "circle"
        }
    ]
}
```
{% endcode %}
