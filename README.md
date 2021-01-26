![header](https://user-images.githubusercontent.com/74942333/105779240-33800000-5f6e-11eb-8eb9-036a71b7966b.png)

Home Assistant ([open source home automation platform focused on local control and privacy](https://www.home-assistant.io/)) - configuration and documentation for my Smart Home. I run my instance on Raspberry Pi 3B+, if you want to do some integration or automation as I did, remember to not copy line to line, you have to understand the code to properly install it - if you have any problems, contact me, I will try to help you as best as I can.


# Software

For starters, I use Hassio installation.

## Automations

For my automations, I mostly use [Node-Red](https://nodered.org) through the hassio integration, although for some simple YAML automations, I use the integrated hassio [component](https://www.home-assistant.io/docs/automation/). This combination works perfectly - Node-Red allows you to create huge and complex automations, and the hassio component works great for simple automation and allows you to use community pre-built automations through [the blueprints](https://www.home-assistant.io/docs/automation/using_blueprints/) feature.

## Integrations installed

* [ESPHome](https://www.home-assistant.io/integrations/esphome/)
* [Hass.io Google Drive Backup](https://github.com/sabeechen/hassio-google-drive-backup)
* [Mosquitto broker](https://github.com/home-assistant/addons/blob/master/mosquitto/DOCS.md)
* [Node-RED](https://community.home-assistant.io/t/home-assistant-community-add-on-node-red/55023)
* [Samba share](https://www.home-assistant.io/hassio/haos_common_tasks/)
* [TasmoAdmin](https://community.home-assistant.io/t/home-assistant-community-add-on-tasmoadmin/54155)
* [Terminal & SSH](https://community.home-assistant.io/t/home-assistant-community-add-on-ssh-web-terminal/33820)






### Hardware
