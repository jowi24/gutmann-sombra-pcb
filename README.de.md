🇬🇧 [English](README.md) · 🇩🇪 **Deutsch**

# gutmann-sombra-pcb

Hardware, um eine Dunstabzugshaube (Gutmann Sombra) in die Hausautomation
einzubinden: eine ESP8266-Platine (ESP-12E), die im Kabel zwischen
Haubenelektronik und Bedienfeld sitzt. Sie liest die LEDs des Bedienfelds
mit und kann Tastendrücke nachbilden – das Original-Bedienfeld funktioniert
dabei unverändert weiter.

- KiCad-10-Platine, 80 × 55 mm, bis auf das ESP-12E-Modul bedrahtet (THT)
- Versorgung über den Service-Anschluss der Haube (~4,8 V) mit
  Buck-Boost-Wandler
- Pegelwandler für die 5-V-Tastenmatrix der Haube
- Fertigungsdaten liegen bei

## Firmware

| Repository | Stand |
|---|---|
| [gutmann-sombra-esphome](https://github.com/jowi24/gutmann-sombra-esphome) | **Empfohlen.** ESPHome External Component, native Home-Assistant-API |
| [gutmann-sombra-mqtt](https://github.com/jowi24/gutmann-sombra-mqtt) | Arduino/PlatformIO, MQTT mit Home-Assistant-Discovery. Wird nicht mehr gepflegt |

Beide laufen auf derselben Platine und lassen sich per OTA gegeneinander
tauschen.

## Dokumentation

| Dokument | Inhalt |
|---|---|
| [Wie die Schaltung funktioniert](docs/CIRCUIT.de.md) | Verständliche Erklärung: Tastenmatrix der Haube, Pegelwandler, Stromversorgung, Firmware-Timing, Fehlersuche |
| [Hardware-Designnotizen](kicad/DESIGN.de.md) | Bauteilwerte, Beschaffung, Layout-Entscheidungen, Inbetriebnahme-Befunde |
| [Fertigungsdaten](kicad/fab/FAB.de.md) | Gerber/Bohrdaten und Bestellparameter |
| [Schaltplan](kicad/schematic.pdf) · [Layout](kicad/board-layout.pdf) | PDF-Exporte |

Alle Dokumente gibt es auch auf Englisch (`*.md` ohne `.de`).

## Stand

Platine Rev. 0.3. Die gefertigten Rev.-0.2-Platinen laufen mit einer
Nachrüstung an U3 (Dioden + Pull-downs, siehe
[DESIGN.de.md](kicad/DESIGN.de.md)).

## Projektstruktur

```
kicad/                Schaltplan, Platine, eigene Footprints und 3D-Modelle
kicad/fab/            Fertigungsdaten
docs/                 Beschreibung der Schaltung
fritzing/             Lochraster-Version von 2017 (nur noch als Referenz)
```

## Erstes Flashen

Neue Platinen werden seriell über J2 geflasht (3,3-V-USB-Seriell-Adapter),
dazu Jumper J5 auf FLASH; danach J5 zurück auf RUN und Reset drücken.
Siehe [CIRCUIT.de.md](docs/CIRCUIT.de.md), Abschnitt 10. Alle späteren
Updates laufen per WLAN.

## Hintergrund

Blog-Artikel zur ursprünglichen Lochraster-Version:
[Do-It-Yourself IoT Modul für die Dunstabzugshaube](https://joachim-wilke.de/blog/2017/12/27/do-it-yourself-iot-modul-fur-die-dunstabzugshaube/)

## Lizenz

Copyright (c) 2017–2026 Joachim Wilke. Hardware und Dokumentation stehen
unter [CC BY-NC-SA 4.0](LICENSE) und sind nur für **nicht-kommerzielle**
Zwecke frei. Kommerzielle Nutzung (z. B. Verkauf von Platinen, Bausätzen
oder darauf basierenden Produkten) erfordert die Zustimmung des Autors.
