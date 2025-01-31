---
icon: router
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# Интернет

### zapret

{% stepper %}
{% step %}
Перейдите в режим рабочего стола и откройте терминал `Konsole`.
{% endstep %}

{% step %}
Отключите `read-only` режим:

{% code overflow="wrap" %}
```bash
sudo steamos-readonly disable
```
{% endcode %}
{% endstep %}

{% step %}
Следуйте [инструкции по установке](../arch/ethernet.md#zapret).
{% endstep %}

{% step %}
Снова включите `read-only` режим:

```bash
sudo steamos-readonly enable
```
{% endstep %}
{% endstepper %}
