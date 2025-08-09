---
icon: gear-complex
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: false
  pagination:
    visible: false
  metadata:
    visible: true
---

# Разное

Автоматическая разблокировка LUKS шифрования через TPM:

{% code overflow="wrap" %}
```sh
sudo systemd-cryptenroll --tpm2-device=auto /dev/nvme1n1p3
```
{% endcode %}
