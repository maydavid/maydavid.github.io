---
title: Wireless Home Environment Monitoring
nav: projects
subnav: wireless_home
layout: default
---

---

# Why?
The idea to develop this project came up as we had a unusual high humidity in our flat in the winter times. The old and leaky windows in our flat have been replaced with new ones. Suddenly there was no more air circulation in our flat and the humidity was going up very high. With the result that mould arose in the corners of the rooms. To lower the humidity in the flat, especially during winter times, it is very important to have a very rigorous controlled airing system. Rush airing and transverse ventilation are the only possibilities to avoid moist walls.

But, as you do not want to think of airing all the time a intelligent solution was required:

+ Automatic opening and closing of windows is not possible, but at least you want to be reminded, when you have to open them
+ Temperature and humidity should be sensed in every room, and stored for statistic evaluation 
+ Mobile access to current and historical data

# How?

Fortunately, several solutions already existed. I only had to select and combine and modify them to my needs.

### Data Processing

For storing the sensor values and a nice graphical representations as well as mobile access, I am using [emoncms.org](http://emoncms.org). It is part of the [open energy monitor](http://openenergymonitor.org) project.

> "Emoncms is a powerful open-source web-app for processing, logging and visualising energy, temperature and other environmental data."

![emoncms_graph](http://emoncms.org/Modules/site/docs/files/visualisations/multigraph.png)


### Sensor Nodes

The sensors are based on the [tinyTX](http://nathan.chantrell.net/tinytx-wireless-sensor/) modules from Nathan Chantrell. The modules are Arduino compatible. I modified them to have the ISP connector on board and used the smd version of the ATtiny.

<div class="projectthumb"><a href="/img/tinysense_node_opt.jpg"><img src="/img/tinysense_node_opt.jpg" width="780" class="tinysense_node" /></a></div>

The main components are:

+ Atmel ATtiny84 
+ HopeRF RFM12B transceiver 
+ DHT22 temperature/humidity sensor

Once a minute the sensors capture temperature, humidity and battery level and transmits them to the base station. In the mean time the ATtiny goes into low-power sleep mode in order to save power.

### Base Station

A raspberry pi is used as the base station. To receive the sensor values I connected one of the sensor nodes to the RPI running a receiver sketch. Most is adapted from [Martin Harizanov](http://harizanov.com/wiki/wiki-home/rfm2pi-board/) work.

Initially emoncms was running [locally](http://emoncms.org/site/docs/raspberrypihdd) on the Pi. I.e. all sensor data has been stored on the SD card and web-access was handled by the pi. The problem is that SD cards have limited write cycles. So it happened that at one day all my data got lost. So I switched to the ["gateway forward"](http://emoncms.org/site/docs/raspberrypigateway) version. Here, received data is immediately transmitted to the web-app hosted at [emoncms.org](emoncms.org), i.e. the SD card is not used.

<div class="projectthumb"><a href="/img/tinysense_base_opt.jpg"><img src="/img/tinysense_base_opt.jpg" width="780" class="tinysense_base" /></a></div>


# Download

[Node sketch](https://github.com/nathanchantrell/TinyTX/blob/master/TinyTX_DHT22/TinyTX_DHT22.ino)

[Base sketch](https://github.com/mharizanov/RFM2Pi/blob/master/firmware/RFM2Pi_RF12_Demo/TinySensor_RF12_Demo/TinySensor_RF12_Demo.ino)

[Node schematic (coming soon)]()



