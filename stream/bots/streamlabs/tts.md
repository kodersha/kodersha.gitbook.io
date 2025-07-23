# Озвучивание выделенного сообщения на Twitch

<figure><img src="../../../.gitbook/assets/cover-tts.png" alt=""><figcaption></figcaption></figure>

Для Streamlabs Chatbot существует скрипт TheNewTTS, он позволяет боту озвучивать сообщения из чата Twitch голосами Google. С появлением баллов канала, некоторые стримеры обзавелись возможностью озвучивания выделенных сообщений, чтобы иметь такую возможность у себя, я слегка дописала плагин TheNewTTS ([src](https://github.com/LuisSanchez-Dev/TheNewTTS)).

{% file src="../../../.gitbook/assets/ThePointsTTS.zip" %}

Теперь, если в настройках плагина не включена функция `Озвучивать всё`, он будет озвучивать только те самые, выделенные за баллы канала, сообщения чата. В настройках скрипта, во вкладке `TTS Configuration`, выберете русский язык озвучки.

### Озвучивание голосом IVONA Maxim <a href="#d0-be-d0-b7-d0-b2-d1-83-d1-87-d0-b8-d0-b2-d0-b0-d0-bd-d0-b8-d0-b5-d0-b3-d0-be-d0-bb-d0-be-d1-81-d0-b" id="d0-be-d0-b7-d0-b2-d1-83-d1-87-d0-b8-d0-b2-d0-b0-d0-bd-d0-b8-d0-b5-d0-b3-d0-be-d0-bb-d0-be-d1-81-d0-b"></a>

TTS Alerts and Chat ([src](https://github.com/kruiser8/TTS-Alerts-And-Chat)) - похожий на предыдущий скрипт, но с поддержкой голоса IVONA Maxim. Так же, как и предыдущий скрипт, я слегка модифицировала его для озвучивания только выделенных сообщений Twitch, плюс отключила ненужные функции Mixer и YouTube.

В дополнительных настройках не нуждается, работает сразу после установки, однако глянуть настройки всё же рекомендую - в них можно прописать запрещенные слова, заблокировать отдельным фолловерам возможность озвучивать сообщения, настроить вывод выделенных сообщений на экран стрима и прочее.

{% file src="../../../.gitbook/assets/TTSAlertsAndChat.zip" %}

Для использования голоса IVONA придется купить (Или [скачать](https://rutracker.org/forum/viewtopic.php?t=5305939)) отдельную программу - `Speech2Go`.

{% content-ref url="script-install.md" %}
[script-install.md](script-install.md)
{% endcontent-ref %}
