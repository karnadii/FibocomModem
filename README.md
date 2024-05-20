# Fibocom Modem Support for MacOS
A kernel extension for macos to add support for two fibocom modem l850 and l860.
You have to make sure the USB interface for the modem already mapped in your kext. Also you have to make sure the modem goes to usb mode and using ncm/acm protocol. For me t440p user, the both modem l860 and l850 automatically use usb mode, if your device is still in pcie mode, refer to this ssdt/dsdt by @HeySora to change the mode to usb mode https://gist.github.com/HeySora/d720554aa5564a7800de8eca45403ef7

Without this kext actually l860 and l850 modems already supported through their acm/ncm native driver, however it is detected as dial up modem rather than wwan, so you dont have information like signal strength and other misc info from the modem. This kext basically just change the way macos detect the modem, from dial up to wwan. If you happy with dial up interface, you don't have to use this.

Choose only one kext, either FibocomModemL850 or FibocomL860, don't use both since their usb vendorId and productId are the same, you need to add FibocomModemSupport too to your kernel config.plist. If the kext doesn't work, probably you have different hardware version, just edit the info.plist of the kext and match the cbdVersion to your hardware version.

I have tested this on big sur, posibbly can be used in catalina and monterey too. but starting from ventura, apple decided to drop support for wwan and dial up modem. In ventura and sonoma, even though the modem detected in network but there is no ui interface for configuring the connection. there is only option for deleting the service and deactivate the service.

# Screenshoot
## L850
![Screen Shot 2024-05-20 at 12 28 53](https://github.com/karnadii/FibocomModem/assets/18657277/7ec5ad6c-db2f-42f6-a532-c17d62c8a1b3)

## L860
![Screen Shot 2024-05-18 at 03 29 26](https://github.com/karnadii/FibocomModem/assets/18657277/92727a47-da02-4828-89ca-1781f43e3970)
![Screen Shot 2024-05-18 at 03 19 28](https://github.com/karnadii/FibocomModem/assets/18657277/01b1660b-6beb-4a49-95e8-18f3760b9f4a)
![Screen Shot 2024-05-18 at 03 28 55](https://github.com/karnadii/FibocomModem/assets/18657277/c7875be6-cfbe-417c-b2f3-d8dd478c5b05)


# Speedtest
I have antenna problem, so the result is not that good, when I use it on my OpenWRT router, the speed can reach more than 100Mbps
![Screen Shot 2024-05-18 at 21 50 29](https://github.com/karnadii/FibocomModem/assets/18657277/ab9e84b5-37a5-43bc-b3e7-ab760d607d53)

# Setup
You just need to set the wwan like the image bellow, use generic for vendor, and gprs for model, apn you can leave it blank or use 'internet' or your apn of choice. don't forget setting up the dns too, without setting up dns you won't be able to surf internet.
![Screen Shot 2024-05-18 at 21 55 09](https://github.com/karnadii/FibocomModem/assets/18657277/d6aa0bc8-e8ad-45d4-9c3c-6e5553cf04fa)
![Screen Shot 2024-05-18 at 21 55 02](https://github.com/karnadii/FibocomModem/assets/18657277/d0ff65f8-f27a-4c50-b575-419c5c3498bb)

## USB Map
Don't forget to map your USB modem interface before using this, this image only an example, use your own usb map kext.
![Screen Shot 2024-05-17 at 03 37 48](https://github.com/karnadii/FibocomModem/assets/18657277/812abbda-82a8-4f3e-a87f-6b9f19ce0571)
![Screen Shot 2024-05-17 at 03 51 41](https://github.com/karnadii/FibocomModem/assets/18657277/93b0f392-2f67-4f06-abbb-be2e8692bed8)
