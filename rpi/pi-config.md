# Konfiguration von RPi Zero W
## Start von HomeAssistant
1. Folgende Kommandos werden für den Start benötigt, als auch der automatische Start des Systems nach Neustart:
```
systemctl enable install_homeassistant.service
systemctl start install_homeassistant.service
```
## Installation von Mosquitto
1. Paket herunterladen und installieren
```
sudo apt-get install mosquitto mosquitto-clients
```
2. Zum anlegen von Username und Passwort zunächst folgenden Befehl benutzen {name} durch eigenen individuellen Username ersetzen
```
sudo mosquitto_passwd -c /etc/mosquitto/passwd {name}
```
3. Nun öffnet man eine neue Konfigurationsdatei für Mosquitto und sagen ihr, dass sie diese Passwort-Datei verwenden soll, um sich für alle Verbindungen anzumelden
```
sudo nano /etc/mosquitto/conf.d/default.conf
```
wird folgendes eingefügt:
```
allow_anonymous false
password_file /etc/mosquitto/passwd
```
4. Abschließend den Service neustarten:
```
sudo systemctl restart mosquitto
```
