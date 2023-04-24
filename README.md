# Clock Home Assistant Integration

This project aims to modify the ULANZI TC001 clock that is compatible with Home Assistant and displays information on the value of various sensors. The clock is designed to be easy to read and display useful information at a glance.

## Features

- Displays current time, date, himidity and temperature
- Displays more informations throw AWTRIX Light App from various sensors connected to Home Assistant

## Getting Started

To get started with this project, you will need the following:

- A [ULANZI TC001](https://www.ulanzi.com/products/ulanzi-pixel-smart-clock-2882)
- A Home Assistant installation

### Step 1:
You can follow the tutorial of [Smart Home Junkie](https://youtu.be/N0NKPJzGHuA?t=252)
- Flash the ULANZI TC001 and install [AWTRIX Light](https://blueforcer.github.io/awtrix-light/#/flasher)
- Connect the ULANZI TC001 to the network from the wifi hotspot
- Install Mosquitto broker on Home Assistant
- Configure a MQTT User
- Configure the MQTT User from the ULANZI TC001 IP Network Interface
- Verify that the ULANZI TC001 is present in the devices panel:
![awtrix_homeassistant](https://user-images.githubusercontent.com/33576918/233953669-be31a444-31f6-4630-82b2-d28e3a48fbef.png)

### Step 2:
Configure a new custom app to the [ULANZI AWTRIX Light Firmware](https://blueforcer.github.io/awtrix-light/#/api?id=custom-apps-and-notifications)
- From Home Assistant, go to configure in Mosquitto broker:

![image](https://user-images.githubusercontent.com/33576918/233955386-92aff33f-5029-4198-8f90-1ee67654b965.png)

- Define a new custom app, for example 'outsidetemperature', by publish a custom app message:


![image](https://user-images.githubusercontent.com/33576918/233956039-c01e201f-2d2d-486e-83a9-b128b4e6c608.png)


Subject:
```ruby
awtrix_2fc7d8/custom/outsidetemperature
```
Where awtrix_XXXXX correspond to the device name on HomeAssistant

Content:
```ruby
{
 "text": "{{ state_attr('weather.your_weather', 'temperature') | round(0, default=-99) }}",
 "icon": "52787", 
  "color": "F2A900" 
}
```

Click on publish, the app should be pushed to the ULANZI TC001 and the content will be displayed in the list off presented app.
Warning, at this moment, the content of sensor temperature is not filled, the next step will define the content throw automation. 

### Step 3:
Update the sensor value in the new custom app:

- From Home Assistant, go to configure in Automation menu and define an automation that will update the value when the app is displayed on the ULANZI screen:

![Capture d’écran 2023-04-24 à 11 36 07](https://user-images.githubusercontent.com/33576918/233959331-51b60512-6f33-4561-a686-8366caee5ae5.png)

This automation will, when the "Current App" switches to the created application "outsidetemperature", update the content displayed on the screen with the value of the outside temperature present in the Home Assistant Meto application.

Follow the tutorial of [Smart Home Junkie](https://youtu.be/N0NKPJzGHuA?t=596) to find and download icons from ID (https://developer.lametric.com/icons)

Here is the result:

![temperatureApp](https://user-images.githubusercontent.com/33576918/233962280-b6e45012-a0fa-4573-b52b-9ce3ae5b4f5d.gif)

Here are some other examples:

Bitcoin Price:

![bitcoinPriceApp](https://user-images.githubusercontent.com/33576918/233962405-0a1f2acd-31f2-480f-8b75-a8b9722b8712.gif)

Solar Panel Watt:

![solarPanelWattApp](https://user-images.githubusercontent.com/33576918/233962482-f78cd0ea-e59c-4946-bc04-bdf98a60aad3.gif)

## Contributing

Contributions to this project are welcome! If you find a bug, have a feature request, or want to contribute code, please open an issue or pull request on this repository.

## License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.

## Acknowledgements

This project was inspired by [Home Assistant](https://www.home-assistant.io/) and the [Smart Home Junkie](https://youtu.be/N0NKPJzGHuA?t=252)
