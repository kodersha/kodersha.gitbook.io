# nodejs

{% tabs %}
{% tab title="nodejs" %}
{% code title="home/home.nix" overflow="wrap" %}
```nix
{ config, pkgs, ...}:

{
    home.packages = with pkgs; [
        nodejs
    ]
}
```
{% endcode %}

{% code overflow="wrap" %}
```bash
npm set prefix ~/.npm-global
```
{% endcode %}
{% endtab %}
{% endtabs %}
