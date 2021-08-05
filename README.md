### SX127x (LoRa transceiver) driver for MicroPython on ESP8266/ESP32/Raspberry_Pi
[original blog post](https://wei1234c.blogspot.tw/2017/08/sx127x-lora-transceiver-driver-for.html)

This fork of [Wei1234c's drivers](https://github.com/Wei1234c/SX127x_driver_for_MicroPython_on_ESP8266) is (or rather will be) stripped-down to the bare minimum for use with a remote sensor and local receiver.

A number of radio settings influence the range and reliability of a LORA transceiver pair. [Here](https://medium.com/home-wireless/testing-lora-radios-with-the-limesdr-mini-part-2-37fa481217ff) is a good discussion on the topic.

For this driver, the key parameters are as follows:
- frequency (defined by your region and hardware): 169E6, 433E6, 434E6, 866E6, 868E6, 915E6
- tx_power_level (default 2): 0 <= x <=14 (or 2 <= x <=17 with boost - I don't understand yet which is active!)
- bandwidth (default 125e3): Set to lower than the required bin value: (7.8E3, 10.4E3, 15.6E3, 20.8E3, 31.25E3, 41.7E3, 62.5E3, 125E3, 250E3)
- spreading_factor (default 8): 6 <= x <= 12
- coding_rate (default 5): 5 <= x <= 8 (true coding rate in the range 1-4 equals this value minus 4)

Respect the fair-use transmission time per sensor of 30 seconds per day. The Semtec "LORA Calculator" tool gives the airtime (and therefore the minimum time between readings) for different radio settings. Or there's an online tool [here](https://loratools.nl/#/airtime).
