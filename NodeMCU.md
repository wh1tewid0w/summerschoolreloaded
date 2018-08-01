# Konfiguration von NodeMCU ESP8266 mit MQTT

## Herunterladen der richtigen Bibliothek

Arduino (1.8.5) offnen und im Reiter unter "Datei" auf "Voreinstellungen" gehen
und bei den "Zusätzlichen Boardverwalter-URLs" folgenden Link einfügen:
"http://arduino.esp8266.com/stable/package_esp8266com_index.json"
Nun ist man in der Lage das richtige Board und die richtigen Bibliotheken auszuwälen.

## Einfügen der Bibliotheken

Unter dem Reiter "Werkzeuge" "Board" und " Boardverwalter..." das richtige Board (ESP8266) suchen und aufwählen.
Unter dem Reiter "Sketch" "Bibliothek einbinden" und "Bibliotheken verwalten..." bei der suche PubSubClient suchen und runterladen.
Unter "Datei" "Beispiele" "PubSubClient" "mqtt_esp8266" auszuwälen und man bekommt den Beispielcode den wir verwendet haben.

## Code Eigenschaften
