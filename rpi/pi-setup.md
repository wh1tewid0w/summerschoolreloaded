# Installation von RPi Zero W
1. Download von [HASSbian](https://github.com/home-assistant/pi-gen/releases/tag/v.1.3.2)
2. Entpacken
3. Auf microSD-Karte brennen (z.B. mit [Etcher](https://etcher.io/)
4. Remounten
5. Im Ordner "boot" eine Datei mit dem Namen "wpa_supplicant.conf" anlegen. In dieser wird folgendes hinterlegt:
```
country=DE //countrycode
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="{YOURSSID}"
    psk="{YOURPASSWORD}" //bei offenem Netzwerk diese Option weglassen
    key_mgmt=WPA-PSK //bei offenem Netzwerk hier "NONE"
}
```

6. Im selben Ordner eine Datei mit dem Namen "ssh" anlegen
7. microSD unmouten und in Raspberry Pi Zero W stecken
8. Mit Strom verkabeln und kurze Zeit warten
9. Nun kann man sich mithilfe eines ssh-client mit dem Pi verbunden werden
```
Die IP-Adresse lässt sich mithilfe von nmap oder anderen Netzwerk-Scannern herausfinden.
```
