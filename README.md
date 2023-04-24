# Clock Home Assistant Integration

This project aims to modify the ULANZI TC001 clock that is compatible with Home Assistant and displays information on the value of various sensors. The clock is designed to be easy to read and display useful information at a glance.

## Features

- Displays current time, date, himidity and temperature
- Displays more informations throw AWTRIX Light App from various sensors connected to Home Assistant

## Getting Started

To get started with this project, you will need the following:

- A ULANZI TC001 (https://www.ulanzi.com/products/ulanzi-pixel-smart-clock-2882)
- A Home Assistant installation

### Step 1:
You can follow the tutorial of Smart Home Junkie here ( https://www.youtube.com/watch?v=N0NKPJzGHuA&t=524s))
- Flash the ULANZI TC001 and install AWTRIX Light from https://blueforcer.github.io/awtrix-light/#/flasher
- Connect the ULANZI TC001 to the network from the wifi hotspot
- Install Mosquitto broker on Home Assistant
- Configure a MQTT User
- Configure the MQTT User from the ULANZI TC001 IP Network Interface
- Verify that the ULANZI TC001 is present in the devices panel:
![awtrix_homeassistant](https://user-images.githubusercontent.com/33576918/233953669-be31a444-31f6-4630-82b2-d28e3a48fbef.png)




Instructions for setting up the clock and integrating it with Home Assistant can be found in the [documentation](./docs/README.md).

## Contributing

Contributions to this project are welcome! If you find a bug, have a feature request, or want to contribute code, please open an issue or pull request on this repository.

## License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.

## Acknowledgements

This project was inspired by [Home Assistant](https://www.home-assistant.io/) and the [ESP8266/ESP32 OLED Clock](https://github.com/squix78/esp8266-oled-ssd1306) project by squix78.
