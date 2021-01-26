![header](https://user-images.githubusercontent.com/74942333/105779240-33800000-5f6e-11eb-8eb9-036a71b7966b.png)

Home Assistant ([open source home automation platform focused on local control and privacy](https://www.home-assistant.io/)) - configuration and documentation for my Smart Home. I run my instance on Raspberry Pi 3B+, with external access possible by using [nabucasa](https://www.nabucasa.com/). If you want to do some integration or automation as I did, remember to not copy line to line, you have to understand the code to properly install it - if you have any problems, contact me, I will try to help you as best as I can.


# Software

For starters, I use Hassio installation.

## Automations

For my automations, I mostly use [Node-Red](https://nodered.org) through the hassio integration, although for some simple YAML automations, I use the integrated hassio [component](https://www.home-assistant.io/docs/automation/). This combination works perfectly - Node-Red allows you to create huge and complex automations, and the hassio component works great for simple automation and allows you to use community pre-built automations through [the blueprints](https://www.home-assistant.io/docs/automation/using_blueprints/) feature.

## Integrations installed

* [ESPHome](https://www.home-assistant.io/integrations/esphome/) - used for DIY ESP8266 and ESP32 projects.

* [Hass.io Google Drive Backup](https://github.com/sabeechen/hassio-google-drive-backup) - everyday backups my whole config and automatically uploads it to Google Drive, saved my ass a lot of times when sd card broke or some integration wasn't configured properly and I couldn't launch Home Assistant. Install it - believe me, it's necesarry.

* [Mosquitto broker](https://github.com/home-assistant/addons/blob/master/mosquitto/DOCS.md) - used for mqtt sensors (most of which in my case are 433mhz, then converted to mqtt protocol by [Xiaomi RF Bridge](https://pl.aliexpress.com/item/32963397492.html?spm=a2g0o.search0302.0.0.4a125ad4dsrMqQ&algo_pvid=17d12786-55fb-4de9-9419-64336a8c355c&algo_expid=17d12786-55fb-4de9-9419-64336a8c355c-1&btsid=2100bdca16116211147923058e3070&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_)), it's necesarry for my config.

* [Node-RED](https://community.home-assistant.io/t/home-assistant-community-add-on-node-red/55023) - as I wrote before, used for most of my automations, I strongly recommend trying it for your instance.

* [Samba share](https://www.home-assistant.io/hassio/haos_common_tasks/) - this add-on allows me to share my config across my local network so I can easily upload files, custom integrations or change config using my Windows PC.

* [TasmoAdmin](https://community.home-assistant.io/t/home-assistant-community-add-on-tasmoadmin/54155) - this allows me to centrally manage my all Sonoff-Tasmota devices.

* [Terminal & SSH](https://community.home-assistant.io/t/home-assistant-community-add-on-ssh-web-terminal/33820) - setting up an SSH server allows access to your Home Assistant folders with any SSH client. It also includes a command-line tool to access the Home Assistant API. It helps with debugging and accessing files in Home Assistant.

* [Home Assistant Community Store](https://hacs.xyz/) - HACS gives you a powerful UI to handle downloads of all your custom needs. It features Integrations, Plugins, AppDaemon Apps, NetDaemon Apps, Python Scripts, and Themes. Hundreds of them created by our beloved community. Later, in the documentation I will list the integrations I use.

### HACS Integrations

* [Breaking changes](https://github.com/custom-components/breaking_changes) - allows me to see potential breaking_changes in the current published version based on loaded components, preventing from breaking my instance.

* [Sonoff LAN](https://github.com/AlexxIT/SonoffLAN) - with this integration you can control Sonoff devices with eWeLink (original) firmware over LAN and/or Cloud. Really usefull if you don't want to flash your Sonoff devices with Tasmota/ESPHome etc.


## External Access

In my case, I didn't have much time to set up DNS, so I just use [nabucasa](https://www.nabucasa.com/) subscription service. It costs 5$/month and contains not only external access but also full Google Assistant/Alexa voice assistants integration and webhooks management. Easy to setup and use, I recommend.

# User Interface

There's a lot to write about my UI, but long story short it's mostly based on Smartphone usage. Even though I spent lots of hours on this, I believe in the principle that Smart Home must work even when a user doesn't use UI or Voice Assistants. That's why my automations are as complex as they are.


### Hardware
