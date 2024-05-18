# Fibocom Modem Support for MacOS
A kernel extension for macos to add support for Fibocom modem, currently only support L860-GL model. L850-GL soon, just ordering the modem today, hope it arrive in 3 days.
You have to make sure the USB interface for the modem already mapped in your kext.

Without this kext actually l860-gl already supported through their acm/ncm native driver, however it is detected as dial up modem rather than wwan, so you dont have information like signal strength and other misc info from the modem. This kext basically just change the way macos detect the modem, from dial up to wwan. If you happy with dial up interface, you don't have to use this.

I have tested this on big sur, posibbly can be used in catalina and monterey too. but starting from ventura, apple decided to drop support for wwan and dial up modem.
In ventura and sonoma, even though the modem detected in network but there is no ui interface for configuring the connection. there is only option for deleting the service and deactivate the service.

# Screenshoot
![Screen Shot 2024-05-18 at 03 16 21](https://github.com/karnadii/FibocomModem/assets/18657277/d7951059-3594-46fa-9744-0efdc9416d99)
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
