# Ideas
A bucket list of project ideas

## Bluetooth enabled AM Radio Transmitter

Connect to any radio (e.g. car) and play any music from your phone through bluetooth.

## Network Booster

Increase network download/upload speed (download higher priority) in a rural area. There are 2 solutions:
1. Better antenna selection
2. Use software to network bonding

More details can be found [here](https://github.com/lherman-cs/network-booster)

Ideally, the whole router stack should be replaced with new Rust implementation instead of relying on dnsmasq, dhcpd, hostapd, and wpa_supplicant.

See more details here, https://github.com/not-yet-awesome-rust/not-yet-awesome-rust/issues/95.


## Car's controller

Read telemetry from OBD reader, useful for diagnosis. Since OBD port exposes diagnosis CAN network, it allows some level of access to the car, e.g. windows, car's locks, lights, etc.

Features:
* Dashboard where car has gone in a google maps
* Find car with a compass on android 
* Control car with android
* Debug issues within the car

## Detect intruder from your driveway

Using Wifi sensing to achieve hidden solar-powered sensors with no blindspot. The sensors' outputs can then be aggregated to form a precise location of the intruder. With this precise location, you can deploy a couple of drones to monitor its movement.

Alternatively, we can equip each wifi sensors with a more powerful board that has a hardware accelerated video encoder that's only awaken whenever the Wifi sensing detects something. The hardware stack maybe something like the following:

1. Wifi sensing and bridge: ESP32-C3 ([link](https://www.seeedstudio.com/Seeed-XIAO-ESP32C3-p-5431.html)): 0.2475w  (100% duty cycle for Wifi sensing and Wifi extended network)
2. Video Acquisition: Raspberry Pi zero ($5) for video acquisition: 2.9w (active only when an intruder is detected)

Assuming intruder detection is triggered 10 times a day and active only for 5 minutes each, every day these devices will spend:

1. Wifi sensing and bridge: 0.2475w * 24 hours = 5.94 wh
2. Video Acquisition: 5 minutes * 10 * 2.9w / 60 minutes/hour = 2.42 wh

Total: 5.94wh + 2.42wh = 8.36wh

A lifepo4 battery like [this one](https://www.amazon.com/Rechargeable-Batteries-Flashlight-Doorbells-Headlamps/dp/B0B1H1YY38/ref=asc_df_B0B1H1YY38/?tag=hyprod-20&linkCode=df0&hvadid=598281370702&hvpos=&hvnetw=g&hvrand=11572138756478888654&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9013365&hvtargid=pla-1762101332841&psc=1) should be plenty for operating a whole day without sunlight

## Peer-to-peer task management

Similar to Brave's chain sync. But, instead of syncing user's history, bookmark, etc. We're storing user task managements. There's also a project called https://syncthing.net/, which stores any files. 

This allows small groups to collaborate with the expense of storing data in the cloud.
