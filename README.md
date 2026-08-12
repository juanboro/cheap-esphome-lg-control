# cheap-esphome-lg-control

This repository documents two low-cost DIY ways to create an interface for [esphome-lg-controller](https://github.com/JanM321/esphome-lg-controller).


## UART <-> LIN Adapter
The first method is to use a low-cost TTL UART to LIN transciever adapter.  These can be bought on Amazon or Aliexpress from various sellers.  I obtained mine on sale for $1 including shipping.

Materials needed:
* ESP32 board (any variant should do - easily obtained from Amazon or Aliexpress)
* 3.3V TTL UART LIN adapter
* Dupont wires/connectors
* Optional: other sensors/etc to hook to ESP32 (i.e: [low cost temperature-humidity sensor](https://esphome.io/components/sensor/dht/))
* Optional: Voltage regulator board (i.e: [these](https://www.amazon.com/dp/B0FDB25T5L))

The challenge with using the adapter is because of the slow baud rate, the LIN bus adapter will time out when the transmit line is held low too long.  I have documented how this can be worked around [here](doc/Low_baud_linxcvr_workaround.md).

To make this work with the ESPHome LG controller - just customize the following yaml file: [esp32_example_uart_lin_xcvr.yaml](esphome/esp32_example_uart_lin_xcvr.yaml) to your own setup.

My basic working example setup before placing in project junction box is pictured [here](doc/images/lg_hvac_lin_xcvr_working.jpg)


## Discrete LG controller level-shift interface
* No need to LIN transceiver Silicon - can just use 2 Mosfets to handle level shifting.
* Will add details soon
