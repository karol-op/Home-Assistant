![header](https://user-images.githubusercontent.com/74942333/105779240-33800000-5f6e-11eb-8eb9-036a71b7966b.png)

Home Assistant ([open-source home automation platform focused on local control and privacy](https://www.home-assistant.io/)) - configuration and documentation for my Smart Home. I run my instance on Raspberry Pi 3B+. If you want to do some integration or automation as I did, remember to not copy line to line, you have to understand the code to properly install it - if you have any problems, contact me, I will try to help you as best as I can.


## Most important principles while building for me

* Smart Home must work even when a user doesn't use UI or Voice Assistants - that's why automations must be complex and be able to react to different scenarios/events.

* Different UI for a different type of devices 


# Software

### Addons installed

* [ESPHome](https://www.home-assistant.io/integrations/esphome/) - used for DIY ESP8266 and ESP32 projects.

* [Hass.io Google Drive Backup](https://github.com/sabeechen/hassio-google-drive-backup) - everyday backups my whole config and automatically uploads it to Google Drive. Install it - believe me, it will save you someday ;)

* [Mosquitto broker](https://github.com/home-assistant/addons/blob/master/mosquitto/DOCS.md) - used for mqtt sensors (most of which in my case are 433mhz, then converted to mqtt protocol by [Xiaomi RF Bridge](https://pl.aliexpress.com/item/32963397492.html?spm=a2g0o.search0302.0.0.4a125ad4dsrMqQ&algo_pvid=17d12786-55fb-4de9-9419-64336a8c355c&algo_expid=17d12786-55fb-4de9-9419-64336a8c355c-1&btsid=2100bdca16116211147923058e3070&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_)).

* [Node-RED](https://community.home-assistant.io/t/home-assistant-community-add-on-node-red/55023) - used for most of my automations

* [Samba share](https://www.home-assistant.io/hassio/haos_common_tasks/) - this add-on allows me to share my config across my local network so I can easily upload files, custom integrations or change config using my PC.

* [TasmoAdmin](https://community.home-assistant.io/t/home-assistant-community-add-on-tasmoadmin/54155) - this allows me to centrally manage all Sonoff-Tasmota devices.

* [Terminal & SSH](https://community.home-assistant.io/t/home-assistant-community-add-on-ssh-web-terminal/33820) - setting up an SSH server allows access to your Home Assistant folders with any SSH client. It also includes a command-line tool to access the Home Assistant API. It helps with debugging and accessing files in Home Assistant.

* [Home Assistant Community Store](https://hacs.xyz/) - HACS gives you a powerful UI to handle downloads of all your custom needs. It features Integrations, Plugins, AppDaemon Apps, NetDaemon Apps, Python Scripts, and Themes. Hundreds of them created by our beloved community. 

* [Vaultwarden](https://github.com/dani-garcia/vaultwarden) - self hosted Bitwarden password manager.

* [DuckDNS](https://github.com/home-assistant/addons/blob/master/duckdns/README.md) and [NGINX proxy](https://github.com/home-assistant/addons/tree/master/nginx_proxy) - used for exposing Vaultwarden to the outside world




### HACS Integrations

* [Breaking changes](https://github.com/custom-components/breaking_changes) - allows me to see potential breaking_changes in the current published version based on loaded components, preventing from breaking my instance.

* [Sonoff LAN](https://github.com/AlexxIT/SonoffLAN) - with this integration you can control Sonoff devices with eWeLink (original) firmware over LAN and/or Cloud.  Useful if you don't want to flash your Sonoff devices with Tasmota/ESPHome etc.

* [Waste collection schedule](https://github.com/mampfes/hacs_waste_collection_schedule) - allows me to retrieve data about my local waste collection

### Automations

For my automations, I mostly use [Node-Red](https://nodered.org) through the hassio integration, although for some simple YAML automations, I use the integrated hassio [component](https://www.home-assistant.io/docs/automation/). This combination works perfectly - Node-Red allows you to create huge and complex automations, and the hassio component works great for simple automation and allows you to use community pre-built automations through [the blueprints](https://www.home-assistant.io/docs/automation/using_blueprints/) feature.


### Tracking users location

One of the most important things in my instance as it allows me to do 99% of the automation without user input.


* GPS Tracking on Mobile Apps of users - my household members and I use [Android Home Assistant app](https://play.google.com/store/apps/details?id=io.homeassistant.companion.android&hl=en&gl=US).

* Wi-Fi Tracking - it's executed in two ways:

  1. Pinging phones every 20 seconds through simple Node-Red automation. It has one disadvantage - you can only say if a device is at home, but you can't predict if a device has left a house (users can turn off their wifi, they may leave their devices at home, phones may not respond to pings etc).
  
  2. Wi-Fi connection status from [Android Home Assistant app](https://play.google.com/store/apps/details?id=io.homeassistant.companion.android&hl=en&gl=US). It tells me what wifi network the phone is currently connected to.



* BLE Tracking - My household members have smartwatches, which emit BLE Signals. I detect them using ESP32 flashed with ESPHome, using [ble_presence platform](https://esphome.io/components/binary_sensor/ble_presence.html). 


### External Access

I just use [nabucasa](https://www.nabucasa.com/) subscription service. It doesn't cost a lot and also gives me full Google Assistant/Alexa voice assistants integration and webhooks management. Easy to set up and use.


### Notifications

They are done with mobile apps + [telegram bot](https://www.home-assistant.io/integrations/telegram/). On telegram, I only get notifications with photos and/or videos attached, and the mobile app works for text-only notifications. Works well and reliably. I'm also using text to speech on Google Speakers, for example, "XYZ is near home".
# User Interface

There's a lot to write about my UI, but long story short it's mostly based on simplicity and has (will have :P) different dashboards for different types of devices.
I fully transitioned to Lovelace UI, it's easy to set up and gives you a lot of opportunities through custom components. For example, not a long time ago I created a settings tab, where through the interface you can enable/disable Christmas UI and automations.

### UI HACS Integrations

* [Lovelace Swipe Navigation](https://github.com/maykar/lovelace-swipe-navigation) - swipe through Lovelace views on mobile, essential for me.

* [layout-card](https://github.com/thomasloven/lovelace-layout-card) - get more control over the placement of Lovelace cards.

* [weather-card](https://github.com/bramkragten/weather-card) - weather card with animated icons, I use it with [open weather map API](https://openweathermap.org/)

* [Mini Media Player](https://github.com/kalkih/mini-media-player) - minimalistic media card, at this time I don't use it but it offers lots of cool features to your UI

### Other UI Integrations

* [Mini Graph Card](https://github.com/kalkih/mini-graph-card) - a minimalistic and customizable graph card, looks great, easy to set up
### How does it look?

Screenshots are on the bottom.

# Hardware

## Xiaomi Ecosystem

It is a great way to start your adventure with Smart Home on a budget. 

To get it working you need to have [Xiaomi Gateway](https://pl.aliexpress.com/item/32952650225.html?spm=a2g0o.productlist.0.0.7fbc71a3i08OF1&algo_pvid=901cf0be-194d-4d66-ad51-207d61882c5b&algo_expid=901cf0be-194d-4d66-ad51-207d61882c5b-14&btsid=2100bdf016119248600463098e74d0&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_). 

<img src="https://user-images.githubusercontent.com/74942333/106276517-fb134700-6237-11eb-8eb5-5326ea749a91.jpg" width="300" height="300">




It's a Zigbee hub that you can connect to Home Assistant using [built-in integration](https://www.home-assistant.io/integrations/xiaomi_miio/).

#### Devices connected to my gateway:
* [Motion Sensor](https://pl.aliexpress.com/item/4000015856327.html) x1

<img src="https://user-images.githubusercontent.com/74942333/106276958-9e645c00-6238-11eb-9506-63a88331eeb7.jpg" width="200" height="200">


* [Wireless Mini Switch](https://pl.aliexpress.com/item/4001042438615.html?spm=a2g0o.productlist.0.0.70437cafxLIUMU&algo_pvid=e431f23e-50a3-4f18-99c5-e6ae18eabe05&algo_expid=e431f23e-50a3-4f18-99c5-e6ae18eabe05-5&btsid=0b0a0ae216119245079724924e17f5&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_) x1

<img src="https://user-images.githubusercontent.com/74942333/106277183-f307d700-6238-11eb-8e3c-cdb18571156e.png" width="200" height="200">


## Switches / Lights

* [Shelly 1](https://shelly.cloud/products/shelly-1-smart-home-automation-relay/) x2

<img src="https://user-images.githubusercontent.com/74942333/106292297-f311d200-624c-11eb-9690-a639953c3dcc.jpg" width="200" height="200">

* [Shelly 2.5](https://shelly.cloud/products/shelly-25-smart-home-automation-relay/) x2

<img src="https://user-images.githubusercontent.com/74942333/106278743-893cfc80-623b-11eb-9304-a51a246eaede.jpg" width="200" height="200">

I chose Shelly, mainly because they can work along with traditional light switches. Home Assistant down? Not a problem, you can still use your lights. They are connected through [Shelly HACS Component](https://github.com/StyraHem/ShellyForHASS), [official shelly integration](https://www.home-assistant.io/integrations/shelly) and one of them is flashed with [Tasmota](https://tasmota.github.io/docs/).


* [Sonoff Touch](https://www.itead.cc/sonoff-touch.html) x1
<img src="https://user-images.githubusercontent.com/74942333/106293041-d3c77480-624d-11eb-9fda-4e56b7507a5c.jpg" width="200" height="200">

Flashed with [ESPEasy](https://github.com/letscontrolit/ESPEasy).

## Motion Sensors

* [433MHZ Digoo Motion Sensor](https://www.amazon.com/DIGOO-Wireless-Infrared-Detector-Security/dp/B074FXWGWP/ref=cm_cr_arp_d_product_top?ie=UTF8) x6 (connected using Modified Xiaomi RF Bridge)

<img src="https://user-images.githubusercontent.com/74942333/106293600-7bdd3d80-624e-11eb-8870-b71ab29c2f17.png" width="200" height="200">


## Temperature Sensors

* [Xiaomi Bluetooth Temperature and Humidity sensor](https://pl.aliexpress.com/item/1005001840988613.html?spm=a2g0o.search0302.0.0.5678540aqnfQ6p&algo_pvid=5aa90c73-b2b3-4021-ba9a-859a20b142be&algo_expid=5aa90c73-b2b3-4021-ba9a-859a20b142be-17&btsid=0b0a187b16118767255823516e8de7&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_) x2 (connected using ESP32BLE DIY project)

<img src="https://user-images.githubusercontent.com/74942333/106294253-3cfbb780-624f-11eb-9691-d4abfe3afebc.JPG" width="200" height="200">

## Cameras

* [EZVIZ MINI PANO 3MP 360°](https://www.ezvizlife.com/uk/item/ez360-Pano/798) x2 (connected through [WebRTC integration.](https://github.com/AlexxIT/WebRTC)

<img src="https://user-images.githubusercontent.com/74942333/106294160-1d648f00-624f-11eb-8143-44bdc24c2113.jpg" width="200" height="200">

## Wall Plugs

* [Sonoff S26 EU](https://sonoff.tech/product/wifi-smart-plugs/s26) x1 (connected through Sonoff Lan custom integration)

<img src="https://user-images.githubusercontent.com/74942333/106294600-a4b20280-624f-11eb-8ef9-7f76fc7e224f.jpg" width="200" height="200">

## TV

* LG, connected through [webostv integration](https://www.home-assistant.io/integrations/webostv/)

<img src="https://user-images.githubusercontent.com/74942333/106294820-ed69bb80-624f-11eb-9be2-b274543edf72.jpg" width="200" height="200">


## Doorbell 

* Normal, dumb couple dollars wireless 433mhz doorbell, connected to Home Assistant using modified Xiaomi RF Bridge.


## DIY Projects

### ESP32 Bluetooth Gateway

An ESP32 flashed with ESPHome. It's used for:
* Tracking, with [ble_presence platform](https://esphome.io/components/binary_sensor/ble_presence.html). It scans for BLE Signals emitted by tracking devices ([iTag](https://www.aliexpress.com/w/wholesale-itag-bluetooth-tracker.html) or Smart Bands/Smart Watches).

* Temperature sensor hub. Collects all the data from [Xiaomi Bluetooth Temperature and Humidity sensor](https://pl.aliexpress.com/item/1005001840988613.html?spm=a2g0o.search0302.0.0.5678540aqnfQ6p&algo_pvid=5aa90c73-b2b3-4021-ba9a-859a20b142be&algo_expid=5aa90c73-b2b3-4021-ba9a-859a20b142be-17&btsid=0b0a187b16118767255823516e8de7&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_) using [Xiaomi Mijia BLE Sensors component](https://esphome.io/components/sensor/xiaomi_ble.html) from ESPHome.

### Xiaomi RF Bridge Modification

[Xiaomi RF Bridge](https://pl.aliexpress.com/item/32963397492.html?spm=a2g0o.search0302.0.0.4a122edc9mQI1s&algo_pvid=ea108c23-dfb3-4c19-9ed1-f65401f41cac&algo_expid=ea108c23-dfb3-4c19-9ed1-f65401f41cac-1&btsid=2100bdde16119184458272994e65fe&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_) flashed with Tasmota, using [this tutorial](https://tasmota.github.io/docs/devices/Sonoff-RF-Bridge-433/). Most of my motion sensors are 433Mhz, so this mod allows me to use them. You can not only receive 433mhz signals but you can send them, for example, you can use this bridge instead of your 433mhz pilot for a gate.



# UI PICTURES




