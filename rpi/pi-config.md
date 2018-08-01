# Konfiguration von RPi Zero W
## Start von HomeAssistant
1. Folgende Kommandos werden für den Start benötigt, als auch der automatische Start des Systems nach Neustart:
```
systemctl enable install_homeassistant.service
systemctl start install_homeassistant.service
```
## Installation von Mosquitto
Für MQTT über HomeAssistant wird ein dedizierter Broker verwendet, hier Mosquitto.

1. Paket herunterladen und installieren
```
sudo apt-get install mosquitto mosquitto-clients
```
2. Zum anlegen von Username und Passwort zunächst folgenden Befehl benutzen {name} durch eigenen individuellen Username ersetzen
```
sudo mosquitto_passwd -c /etc/mosquitto/passwd {name}
```
4. Hier wird gebeten ein Passwort festzulegen
5. Nun öffnet man eine neue Konfigurationsdatei für Mosquitto und sagen ihr, dass sie diese Passwort-Datei verwenden soll, um sich für alle Verbindungen anzumelden
```
sudo nano /etc/mosquitto/conf.d/default.conf
```
wird folgendes eingefügt:
```
allow_anonymous false
password_file /etc/mosquitto/passwd
```
6. Abschließend den Service neustarten:
```
sudo systemctl restart mosquitto
```
## MQTT Konfiguration für HomeAssistant
`Die configuration.yaml befindet sich hier: /home/homeassistant/.homeassistant/configration.yaml`
1. In der Konfigurationsdatei wird am Dateiende folgendes hinzugefügt:
```
mqtt:
 broker: 127.0.0.1        //hier intern auf gleichem System wie HASS, falls extern, hier externe IP angeben
 port: 1883               //Port worüber Mosquitto angesprochen wird
 username: {username}     //zuvor individuell angegebener Username
 password: {password}     //zuvor festgelegtes Passwort

```
