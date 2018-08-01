# Konfiguration von RPi Zero W
## Start von HomeAssistant
1. Folgende Kommandos werden für den Start benötigt, als auch der automatische Start des Systems nach Neustart:
```bash
systemctl enable install_homeassistant.service
systemctl start install_homeassistant.service
```
## Installation von Mosquitto
Für MQTT über HomeAssistant wird ein dedizierter Broker verwendet, hier Mosquitto.

1. Paket herunterladen und installieren
```bash
sudo apt-get install mosquitto mosquitto-clients
```
2. Zum anlegen von Username und Passwort zunächst folgenden Befehl benutzen {name} durch eigenen individuellen Username ersetzen
```
sudo mosquitto_passwd -c /etc/mosquitto/passwd {name}
```
4. Hier wird gebeten ein Passwort festzulegen
5. Nun öffnet man eine neue Konfigurationsdatei für Mosquitto und sagen ihr, dass sie diese Passwort-Datei verwenden soll, um sich für alle Verbindungen anzumelden
```bash
sudo nano /etc/mosquitto/conf.d/default.conf
```
wird folgendes eingefügt:
```
allow_anonymous false
password_file /etc/mosquitto/passwd
```
6. Abschließend den Service neustarten:
```bash
sudo systemctl restart mosquitto
```
## MQTT Konfiguration für HomeAssistant
`Die configuration.yaml befindet sich hier: /home/homeassistant/.homeassistant/configration.yaml`
1. In der Konfigurationsdatei wird am Dateiende folgendes hinzugefügt:
```yaml
mqtt:
 broker: 127.0.0.1        //hier intern auf gleichem System wie HASS, falls extern, hier externe IP angeben
 port: 1883               //Port worüber Mosquitto angesprochen wird
 username: {username}     //zuvor individuell angegebener Username
 password: {password}     //zuvor festgelegtes Passwort

```
2. Nun muss noch ein sogenannter "Sensor" angelegt werden
```yaml
sensor:
  - platform: mqtt        //Benutzte Plattform
    state_topic: topic    //Notwendig, sozusagen der Name des Kanals
```
3. Zuletzt muss ein Switch, also ein Schalter angelegt werden welcher z.B. per 433mHz Aus- und Einschaltcodes versendet
```yaml
switch:
  - platform: rpi_rf                                      //Benutzte Plattform
    gpio: 02                                              //Data-Pin des angeschlossenen 433mHz Transmitters
    switches:                                                 
     steckdose_1:                                         //Individueller Name
      pulselength: 400                                    //Delay
      protocol: 5                                         //Protocol-Typ
      code_on: 12800688, 12884272, 13311296, 13574512     //Einschaltcodes
      code_off: 13202192, 13125520, 13098656, 12961312    //Ausschaltcodes
```
4. Um die Änderungen wirksam zu machen muss HomeAssistant neugestartet werden. Dies geschiet entweder über die Einstellungen im Webinterface, oder über die Konsole bei Neustart des Services
