# Installation und Konfiguration von RPi Zero W

1. Download von [HASSbian](https://github.com/home-assistant/pi-gen/releases/tag/v.1.3.2)
2. Entpacken
3. Auf microSD-Karte brennen (z.B. mit [Etcher](https://etcher.io/)
4. Remounten
5. Im Ordner "boot" eine Datei mit dem Namen "wpa_supplicant.conf" anlegen
* In dieser wird folgendes hinterlegt:
```
country=DE
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="summerschool"
    psk="summerschool"
    key_mgmt=WPA-PSK
}
```
