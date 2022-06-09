---
layout: post
current: post
cover:  assets/images/esp8266-temperature-monitoring/temperature-monitor.jpeg
navigation: True
title: Temperature sensors with display and alerting for marine aquarium
date: 2022-05-01 06:00:00
tags: [ELECTRONIC, ESP8266, MARINE-AQUARIUM]
class: post-template
subclass: ‚post‘
author: tschminkel
---

In marine fishkeeping the water temperature belongs to the important and easy to monitor water parameters that can be monitored electronically very easy. The temperature is strongly dependent from the room temperature and influenced by other equipment like UV-C clearer and lighting in particular if the LEDs are sitting close to the water surface. Inappropriate water temperature, meaning out of the rage of 23 to 28 °C can lead to damage or even death of the fishes and the corals.

In order to monitor the temperature I build a small device with two temperature sensors that will constantly monitor the temperature at two different places in the aquarium. You don’t need your mobile all the time, the values can be checked at the display of the device and if the temperature leaves a defined range of 24-27 °C you get notified. The device has got a physical notification. That means a buzzer starts beeping and you can pause the notification by pressing the snooze button for defined period of time.

![Temperature Sensor Case Open](/assets/images/esp8266-temperature-monitoring/temperature-case-open.jpeg)

Now lets have a look at the list of part I used:

| &nbsp;##&nbsp; | Parts                                                      | Amazon.de                              |
| -------------- | ---------------------------------------------------------- | -------------------------------------- |
| 1              | 1 x D1 Mini D1 Mini V3 NodeMCU ESP8266EX                   | [Amazon-Link](https://amzn.to/3uMy4G6) |
| 2              | 1 x OLED display shield I2C SSD1306                        | [Amazon-Link](https://amzn.to/3oMWyew) |
| 3              | 2 x Temperature Sensor - 3M Kabel DS18B20                  | [Amazon-Link](https://amzn.to/3oJizKU) |
| 4              | 1 x Box, Electronic Enclosure, Waterproof (89 x 59 x 35mm) | [Amazon-Link](https://amzn.to/3oLFntx) |
| 5              | 1 x Round Acryl Sheets, 2 Zoll/ 5 cm                       | [Amazon-Link](https://amzn.to/3JpBNgF) |
| 6              | 1 x UHU 45440 Superglue                                    | [Amazon-Link](https://amzn.to/3oRBx22) |
| 7              | 1 x M12 Cable Fitting                                      | [Amazon-Link](https://amzn.to/3uSa44f) |
| 8              | 1 x KY-012 Piezo Buzzer Alarm                              | [Amazon-Link](https://amzn.to/3Jxmz9E) |
| 9              | 1 x Resistor 470Ω from Resistor Kit                        | [Amazon-Link](https://amzn.to/34JodGj) |
| 10             | 1 x Resistor 10kΩ from Resistor Kit                        | [Amazon-Link](https://amzn.to/34JodGj) |
| 11             | 1 x PCB 7x3cm shortened from Universal Board Kit           | [Amazon-Link](https://amzn.to/3GPJkDW) |
| 12             | 3 x Screw Terminals from Universal Board Kit               | [Amazon-Link](https://amzn.to/3GPJkDW) |
| 13             | 1 x Tactile Push Button 9,5mm from Button Kit              | [Amazon-Link](https://amzn.to/3pcEKtx) |
| 14             | 1 x Micro Cable Electronics Male/Female Connector          | [Amazon-Link](https://amzn.to/36hvU72) |
| 15             | 1 x Universal Power Supply 5V                              | [Amazon-Link](https://amzn.to/3rPPTBU) |

![Temperatur Monitor Electronic Circuit](/assets/images/esp8266-temperature-monitoring/temperature-monitor-fritzing.png)

## NOTIZEN

In der Meerwasseraquaristik gehört die Wassertemperatur sicherlich zu den wichtigen und sehr einfach auch elektronisch messbaren Wasserparametern. Zur Überwachung möchte ich daher ein kleines, autarkes Gerät bauen, das die Temperatur dauerhaft überwacht und bei Über- und Unterschreitung von Schwellwerten informiert. Zusätzlich sollen aktuelle Werte auch am Gerät ablesbar sein, wobei auch deren Aktualität (Zeitstempel) nachvollziehbar sein muss. Eine Integration in die Hausautomatisierung bietet zusätzlich die Möglichkeit der Kontrolle von Remote als auch grafische Auswertungen und Trendanalysen. Los gehts!

- Warum ist die Temperatur im Meerwasseraquarium so wichtig, kurze 2-3 Sätze zur Einleitung
- standalone Gerät
- geschlossenes Gehäuse wegen dem Salzwasser
- wartungsfrei daher Netzteil
- remote Kontrolle daher mqtt auf Homematic (welcher Broker???)
- Aufzeichnung (mqtt nach Influx-DB) via Influx-DB und Auswertung via Grafana, zeitliche Überwachung wichtig, weil ansonsten keinen Überblick bei Überschreitung
- Benachrichtigung bei Überschreitung (auch Unterschreitung) mittels Pushover (alle 10 Minuten eine Nachricht) + Flashing Display (invert, true, false) bei 28 Grad Celsius. Erklären warum 28 Grad so wichtig ist.
- Sprich ab 28 Grad verlassen wir den optimalen Bereich, ab 29,5 Grad wird es hingegen kritisch!!!

## Anforderungen

- 2 Temperaturfühler zum dauerhaften messen der  Wassertemperatur im Meerwasseraquarium.
- Anzeige der Temperaturwerte auf einem Display, um eine direkte Prüfung der Werte zu ermöglichen.
- Benachrichtigung aufs Handy bei Überschreitung eines Schwellwerts von 28 Grad, ggf. ohne HM
- Weitere Anzeige von Datum und Zeit sowie IP-Adresse.
- Übermittlung der Temperaturwerte an eine HomeMatic Zentrale via MQTT.
- Stromversorgung via Netzteil, wartungsfrei ohne Batterien.

## Bau des Geräts

- Bestückung der Platine —> Fritzing Schaltplan erstellen und darstellen
- Bohrungen im Gehäuse vornehmen (welches Bohrset, Link!)
- Acrylglas aufkleben, von hinten

## Anzeige folgender Daten auf einem OLED 64x48 Pixel (zeilenweise)

- Anzeige der Temperatur von Sensor 1. z.B. „1: 23.00 C“
- Anzeige der Temperatur von Sensor 2. z.B. „2: 24.00 C“
- Anzeige Update Zeit. z.B. „30.11.2021 12:05:59“ (2 Zeilen)
- IP Adresse des Sensors. z.B. x.x.x.123

## MQTT publish von folgenden Daten

- /data/aquarium/temp/1 = 23,00 C
- /data/aquarium/temp/2 = 23,00 C
- /data/aquarium/temp/updated = 2021-12-01 12:05:59

## Arduino Environment

- Arduino IDE z.B. Version 1.8.16 installieren
- Board Manager URLs eintragen und D1 mini Board installieren
- „esp8266“ Board suchen  und installieren
- Blink Example Sketch testen

## Stückliste

Gehäuse - wasserdicht `89 * 59 * 35mm` (Waterproof Junction Box @amazon)
Acrylplatte rund - Durchmesser 2 Zoll, d.h. 5cm (Klare Acrylplatte rund @amazon)
ESP8266EX - AZDelivery D1 Mini V3 NodeMCU (AZDelivery D1 Mini V3 ESP8266EX @amazon)
OLED Display - AZDelivery 0,66 Zoll Shield D1 Mini 64X48 (AZDelivery 0,66 Zoll OLED Display @amazon)
Temperatursensoren DS18B20 - AZDelivery 2 x 3M Kabel wasserdicht (AZDelivery DS18B20 @amazon)

## Weitere Quellen

- ESPDateTime (NTP Server Library)
  - <https://github.com/mcxiaoke/ESPDateTime>
- ESP Board Manager URLs
  - <http://arduino.esp8266.com/stable/package_esp8266com_index.json>
  - <https://dl.espressif.com/dl/package_esp32_index.json>
- Wolles Elektronikkiste - Wemos D1 Mini Boards
  - <https://wolles-elektronikkiste.de/wemos-d1-mini-boards>
