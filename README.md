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

Alternatively, we can equip each wifi sensors with a more powerful board that has a hardware accelerated video encoder that's only awaken whenever the Wifi sensing detects something.

