![header](https://user-images.githubusercontent.com/74942333/105779240-33800000-5f6e-11eb-8eb9-036a71b7966b.png)

Home Assistant ([open source home automation platform focused on local control and privacy](https://www.home-assistant.io/)) - configuration and documentation for my Smart Home. I run my instance on Raspberry Pi 3B+. If you want to do some integration or automation as I did, remember to not copy line to line, you have to understand the code to properly install it - if you have any problems, contact me, I will try to help you as best as I can.


## Most important principles while building for me

* Smart Home must work even when a user doesn't use UI or Voice Assistants - that's why automations must be complex and be able to react to different scenarios/events.

* Different UI for a different type of devices (although I mainly focus on mobile)


# Software

For starters, I use Hassio installation.

### Integrations installed

* [ESPHome](https://www.home-assistant.io/integrations/esphome/) - used for DIY ESP8266 and ESP32 projects.

* [Hass.io Google Drive Backup](https://github.com/sabeechen/hassio-google-drive-backup) - everyday backups my whole config and automatically uploads it to Google Drive, saved my ass a lot of times when sd card broke or some integration wasn't configured properly and I couldn't launch Home Assistant. Install it - believe me, it's necessary.

* [Mosquitto broker](https://github.com/home-assistant/addons/blob/master/mosquitto/DOCS.md) - used for mqtt sensors (most of which in my case are 433mhz, then converted to mqtt protocol by [Xiaomi RF Bridge](https://pl.aliexpress.com/item/32963397492.html?spm=a2g0o.search0302.0.0.4a125ad4dsrMqQ&algo_pvid=17d12786-55fb-4de9-9419-64336a8c355c&algo_expid=17d12786-55fb-4de9-9419-64336a8c355c-1&btsid=2100bdca16116211147923058e3070&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_)), it's necessary for my config.

* [Node-RED](https://community.home-assistant.io/t/home-assistant-community-add-on-node-red/55023) - as I wrote before, used for most of my automations, I strongly recommend trying it for your instance.

* [Samba share](https://www.home-assistant.io/hassio/haos_common_tasks/) - this add-on allows me to share my config across my local network so I can easily upload files, custom integrations or change config using my Windows PC.

* [TasmoAdmin](https://community.home-assistant.io/t/home-assistant-community-add-on-tasmoadmin/54155) - this allows me to centrally manage my all Sonoff-Tasmota devices.

* [Terminal & SSH](https://community.home-assistant.io/t/home-assistant-community-add-on-ssh-web-terminal/33820) - setting up an SSH server allows access to your Home Assistant folders with any SSH client. It also includes a command-line tool to access the Home Assistant API. It helps with debugging and accessing files in Home Assistant.

* [Home Assistant Community Store](https://hacs.xyz/) - HACS gives you a powerful UI to handle downloads of all your custom needs. It features Integrations, Plugins, AppDaemon Apps, NetDaemon Apps, Python Scripts, and Themes. Hundreds of them created by our beloved community. Later, in the documentation, I will list the integrations I use.

### HACS Integrations

* [Breaking changes](https://github.com/custom-components/breaking_changes) - allows me to see potential breaking_changes in the current published version based on loaded components, preventing from breaking my instance.

* [Sonoff LAN](https://github.com/AlexxIT/SonoffLAN) - with this integration you can control Sonoff devices with eWeLink (original) firmware over LAN and/or Cloud.  Useful if you don't want to flash your Sonoff devices with Tasmota/ESPHome etc.


### Automations

For my automations, I mostly use [Node-Red](https://nodered.org) through the hassio integration, although for some simple YAML automations, I use the integrated hassio [component](https://www.home-assistant.io/docs/automation/). This combination works perfectly - Node-Red allows you to create huge and complex automations, and the hassio component works great for simple automation and allows you to use community pre-built automations through [the blueprints](https://www.home-assistant.io/docs/automation/using_blueprints/) feature.


### Person Tracking 

One of the most important things in my case because it allows me to set up for example alarm when no one is home. For me tracking is done through:

* GPS Tracking on Mobile Apps of users - my household members and I use [Android Home Assistant app](https://play.google.com/store/apps/details?id=io.homeassistant.companion.android&hl=en&gl=US), it also sends data about battery and lots of other things,  you can choose which ones you want to see in your instance, but be careful with quantity - it might reduce your mobile device battery life drastically.


* Wi-Fi Tracking - it's executed through Node-Red very simple automation. It's pinging the devices every 20 seconds, which allows me to see whose mobile is connected to a local network. You always carry your smartphone with you so it's a very convenient and easy to use method although it has one disadvantage - you can only say if a device is at home, but you can't predict if a device has left a house (it is about turning off wi-fi by household members, loss of coverage or simple discharge of device).



* BLE Tracking - for now, it's used for mine [Mi Band 3](https://www.aliexpress.com/w/wholesale-mi-band-3.html) and [iTag devices](https://www.aliexpress.com/w/wholesale-itag-bluetooth-tracker.html). Mi Band and iTags emit BLE Signals every minute or so allowing me to see if they're at home. I execute it with ESP32-BLE (working as a kind of Bluetooth Gateway) flashed with ESPHome, using [ble_presence platform](https://esphome.io/components/binary_sensor/ble_presence.html). It scans for BLE Signals emitted by devices.


### External Access

In my case, I didn't have much time to set up DNS, so I just use [nabucasa](https://www.nabucasa.com/) subscription service. It costs 5$/month and contains not only external access but also full Google Assistant/Alexa voice assistants integration and webhooks management. Easy to set up and use, I recommend.


### Notifications

They are done with mobile apps + [telegram bot](https://www.home-assistant.io/integrations/telegram/). On telegram I only get notifications with photos and/or videos attached and mobile app work for text only notifications. Works well and reliably. 
# User Interface

There's a lot to write about my UI, but long story short it's mostly based on simplicity and has (will have :P) different dashboards for different types of devices.
I fully transitioned to Lovelace UI, it's easy to set up and gives you a lot of opportunities through custom components. For example, not a long time ago I created a settings tab, where through the interface you can enable/disable Christmas UI and automations.

### UI HACS Integrations

* [Lovelace Swipe Navigation](https://github.com/maykar/lovelace-swipe-navigation) - swipe through Lovelace views on mobile, essential for me.

* [layout-card](https://github.com/thomasloven/lovelace-layout-card) - get more control over the placement of lovelace cards.

* [weather-card](https://github.com/bramkragten/weather-card) - weather card with animated icons, I use it with [open weather map API](https://openweathermap.org/)

* [Mini Media Player](https://github.com/kalkih/mini-media-player) - minimalistic media card, at this time I don't use it but it offers lots of cool features to your UI

### Other UI Integrations

* [Mini Graph Card](https://github.com/kalkih/mini-graph-card) - a minimalistic and customizable graph card, looks great, easy to set up

# Hardware
