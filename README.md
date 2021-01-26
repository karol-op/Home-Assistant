![header](https://user-images.githubusercontent.com/74942333/105779240-33800000-5f6e-11eb-8eb9-036a71b7966b.png)

Home Assistant ([open source home automation platform focused on local control and privacy](https://www.home-assistant.io/)) - configuration and documentation for my Smart Home. I run my instance on Raspberry Pi 3B+, if you want to do some integration or automation as I did, remember to not copy line to line, you have to understand the code to properly install it - if you have any problems, contact me, I will try to help you as best as I can.


# Software

For starters, I use Hassio installation.

## Automations

For my automations, I mostly use [Node-Red](https://nodered.org) through the hassio integration, although for some simple YAML automations, I use the integrated hassio [component](https://www.home-assistant.io/docs/automation/). This combination works perfectly - Node-Red allows you to create huge and complex automations, and the hassio component works great for simple automation and allows you to use community pre-built automations through [the blueprints](https://www.home-assistant.io/docs/automation/using_blueprints/) feature.

## Integrations installed

* [ESPHome](https://www.home-assistant.io/integrations/esphome/) - used for DIY esp8266 and esp32 projects

* [Hass.io Google Drive Backup](https://github.com/sabeechen/hassio-google-drive-backup) - everyday backups my whole config and automatically uploads it to Google Drive, saved my ass a lot of times when sd card broke or some integration wasn't configured properly and I couldn't launch Home Assistant. Install it - believe me, it's necesarry.

* [Mosquitto broker](https://github.com/home-assistant/addons/blob/master/mosquitto/DOCS.md) - used for mqtt sensors (most of which in my case are 433mhz, then converted to mqtt protocol by [Xiaomi RF Bridge](https://pl.aliexpress.com/item/32963397492.html?spm=a2g0o.search0302.0.0.4a125ad4dsrMqQ&algo_pvid=17d12786-55fb-4de9-9419-64336a8c355c&algo_expid=17d12786-55fb-4de9-9419-64336a8c355c-1&btsid=2100bdca16116211147923058e3070&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_)), it's necesarry for my config.

* [Node-RED](https://community.home-assistant.io/t/home-assistant-community-add-on-node-red/55023) - as I wrote before, used for most of my automations, I really recommend trying it for your instance.

* [Samba share](https://www.home-assistant.io/hassio/haos_common_tasks/) - this add-on allows me to share my config across my local network so I can easily upload files, custom integrations or change config using my Windows PC.

* [TasmoAdmin](https://community.home-assistant.io/t/home-assistant-community-add-on-tasmoadmin/54155)

* [Terminal & SSH](https://community.home-assistant.io/t/home-assistant-community-add-on-ssh-web-terminal/33820)






### Hardware
