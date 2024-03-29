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

## Autofill local DNS cache

In referring other computers, we rarely use their IP addresses, they're painful to remember. DNS was created to solve this exact problem. Unfortunately, DNS is usually used only for public services not for local services. We have MDNS, but this requires admin access to the router. 

Each node in the network can be configured to use a local DNS server, which requires the node to run the DNS server locally and configure the network interface to use localhost as the preferred DNS server. 

To fill the local DNS server cache, we can listen to the network broadcast for DHCP offers which include the client's hostname. We also need to allow manual override. Since DHCP offers don't happen often (during initialization and lease expiration), we should run the node implementing this should be running in a long lived session.


## open source High quality vr desktop exclusive for Linux only

Replace traditional monitors with VRs. Instead of wireless, it's required to use a usb cable. Even with usb 2.0, we have 480Mbps, that's 200x more bandwidth than 1080p videos!! 

The software is going to be open source and exclusive for Linux. It should be created for developers in mind.

## Generic tagging LSP Server

Generic tagging refers to a magic format that can be used for quick lookups. A use case would be for note taking, e.g. I want to quickly lookup a person's name by typing "##user", the LSP server is used to integrate with any IDEs to create a nice autocompletion dropdown on the UI. Under the hood, the LSP server can stay stateless, it can use ripgrep to fulfill the query. Perhaps, after the completion, it transforms "##user" to "##user#<person's name>". This will allow ripgrep to quickly dissect the possible matches by looking at the prefix. Possible taggings:
1. ##user#<person's name>
2. ##date#<date in ISO format>
3. ##due_by#<date in ISO format>: it can be used for creating alarms


