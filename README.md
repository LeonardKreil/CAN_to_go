{| width="99%"
 | style="vertical-align:top" |

__NOTOC__
<div style="border: 1px solid black; background-color:lightblue; font-size:1px; height:20px; border-bottom:1px solid 97BF87">
</div>
<div style="border: 1px solid black; background-color:whitesmoke; padding:7px;">
__NOEDITSECTION__
==''Fach''==
'''Vertiefung Microcomputertechnik'''

==''Entwickler''==
'''Michael Graml <br> Leonard Kreil'''

==''Technischer Hintergrund''==
'''CAN-Bus-Überwachung und Diagnose'''

| width="80%" style="vertical-align:top" |
<br>

__INHALTSVERZEICHNIS__

<h2 style="font-size:200%; text-align:center;">Projektbeschreibung 📄</h2>

Das "CAN-TO-GO-SYSTEM" ist eine fortschrittliche Lösung für die Überwachung und Diagnose von CAN-Bussystemen. Es ist darauf ausgelegt, Nutzern bei der Einrichtung und Fehlersuche in CAN-Netzwerken zu assistieren. Das System kombiniert Hardware- und Softwarekomponenten für eine effiziente Analyse und Interaktion mit dem CAN-Netzwerk.

[[Datei:Can to go system.png|300px|center]]

<h2 style="font-size:200%; text-align:center;">Hardware-Aufbau 🔧</h2>

Der Hardwareaufbau des Projekts basiert auf einer sorgfältig entworfenen Leiterplatte, die mit KiCad, einem Open-Source-Tool für PCB-Design, gestaltet wurde. Die Auswahl und Platzierung der elektronischen Bauteile sowie deren Footprints wurden im Schaltplan integriert, wobei besonderes Augenmerk auf die logische Gruppierung und Minimierung der Leitungslängen gelegt wurde, um Effizienz und Signalintegrität zu gewährleisten.

Für die Herstellung wurde die Leiterplatte bei Aisler bestellt und die Bauteile separat von Mouser Electronics bezogen. Die Bestückung erfolgte mittels Lötpaste.

Das Herzstück des Systems bildet der ESP32-Mikrocontroller, der für die Verarbeitung und Koordination aller Aufgaben zuständig ist. Er verbindet wichtige Elemente wie die CAN-Schnittstelle, das Display, Status-LEDs und Taster zu einem funktionierenden Ganzen. Der ESP32 liest und verarbeitet CAN-Bus-Nachrichten und steuert das Display über das I2C-Protokoll, wobei ein Logikpegelwandler für die Anpassung der unterschiedlichen Spannungsniveaus verwendet wird.

Das Display visualisiert wichtige Informationen und kommuniziert über das I2C-Protokoll mit dem ESP32. Da der ESP32 mit 3,3 Volt und das Display mit 5 Volt betrieben wird, wird ein Logikpegelwandler für die Signalübersetzung eingesetzt.

Der SUB-D-Stecker dient zur Integration von CAN-Nachrichten und der MCP2562-E-P Transceiver wandelt Signale des CAN-Busses in digitale Signale um, die vom ESP32 verarbeitet werden können. Verschiedene LEDs dienen als Statusanzeigen, während Taster Benutzerinteraktionen ermöglichen.

Abschließend spielen Bypass-Kondensatoren eine wichtige Rolle bei der Stabilisierung der Versorgungsspannung und der Rauschunterdrückung, um die Funktionalität des Systems zu gewährleisten.

[[Datei:Leiterplate.png|300px|center]]

<h2 style="font-size:200%; text-align:center;">Software 📏</h2>

Die Software des "CAN-TO-GO-SYSTEMS" besteht aus zwei Hauptkomponenten: einem ESP32-Mikrocontroller und einer benutzerfreundlichen GUI. Der ESP32 basiert auf dem espidf-Framework und ist für das Empfangen, Anzeigen und Bereitstellen von CAN-Nachrichten über eine REST-API verantwortlich. Die Softwarearchitektur folgt der Clean Architecture von Robert C. Martin und nutzt FreeRTOS Tasks mit Finite State Machines (FSM) für strukturierte Kontrollabläufe. Die FSM umfasst drei Zustände: STARTING, CONFIGURATION und OPERATION, um das System zu starten, zu konfigurieren und laufend zu prüfen.

Das CAN Repository, eine zentrale Komponente, implementiert Interface Adapter zur Konvertierung von Daten zwischen dem CAN Controller und verschiedenen Use-Cases wie LEDs, Display und REST API. Diese Struktur gewährleistet die Einhaltung des Single Responsibility Principle und sorgt für leichte Wartbarkeit und Erweiterbarkeit der Software.

<div style="display: flex; justify-content: space-around;">
    <div style="flex: 1; padding: 5px;">
        [[Datei:Architekturbild.png|500px]]
    </div>
    <div style="flex: 1; padding: 5px;">
        [[Datei:Fsm.png|500px]]
    </div>
</div>

<h2 style="font-size:200%; text-align:center;">Benutzeroberfläche und Web-Integration 💻</h2>

Das externe User Interface wurde entwickelt, um die begrenzten Möglichkeiten des LCD-Displays zu erweitern und wurde mit Flutter, einem Open-Source-Framework von Google, erstellt. Das UI bietet zwei Hauptfunktionen: einen Overview Tab, der alle empfangenen CAN IDs mit aktuellen Daten und Zykluszeiten anzeigt, und einen Trace Tab, der die letzten empfangenen CAN-Nachrichten visualisiert.

Die Struktur der GUI folgt ebenfalls der Clean Architecture, wobei Datasources Rohdaten von der REST API lesen und Repositories die Daten in listenbasierte Darstellungen für die Tabs umwandeln. Widgets wie CanTable ermöglichen eine flexible Anpassung und Darstellung der CAN-Nachrichten in den verschiedenen Tabs. Die GUI bietet somit eine effiziente und vielseitige Schnittstelle zur Überwachung und Analyse der CAN-Kommunikation.

<div style="display: flex; justify-content: space-around;">
    <div style="flex: 1; padding: 5px;">
        [[Datei:Gui overview.png|500px]]
    </div>
    <div style="flex: 1; padding: 5px;">
        [[Datei:Gui trace.png|500px]]
    </div>
</div>

<h2 style="font-size:200%; text-align:center;">Zukünftige Erweiterungen 🌟</h2>

Das System ist für zukünftige Erweiterungen und Anpassungen konzipiert. Entwickler können zusätzliche Module und Funktionen integrieren, um die Leistungsfähigkeit und Vielseitigkeit des Systems weiter zu erhöhen.

<h2 style="font-size:200%; text-align:center;">Fazit 🔍</h2>

Das "CAN-TO-GO-SYSTEM" stellt eine innovative und flexible Lösung für die Diagnose und Überwachung von CAN-Bussystemen dar. Seine Kombination aus leistungsfähiger Hardware und anpassungsfähiger Software macht es zu einem wertvollen Werkzeug für Fachleute in verschiedenen Bereichen.

==Quellen==
[1] amazon. URL: https://www.amazon.de/gp/product/B07TTNBBSC/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&th=1 (besucht am 30. 12. 2023).
[2] AZ-Delivery. URL: https : / / www . az - delivery . de / products / esp32 - developmentboard(besucht am 27. 12. 2023).
[3] Robert C. Martin. Solid Relevance. Okt. 2020. URL: https : / / blog . cleancoder . com / uncle -bob/2020/10/18/Solid-Relevance.html.
[4] Robert C. Martin. The Clean Architecture. Aug. 2012. URL: https : / / blog . cleancoder . com /uncle-bob/2012/08/13/the-clean-architecture.html.
[5] Robert C. Martin u. a. Clean Architecture: a craftsman’s guide to software structure and design. eng.Robert C. Martin series. Boston Columbus Indianapolis New York San Francisco Amsterdam CapeTown Dubai London Madrid Milan Munich Paris Montreal Toronto Delhi Mexico City São PauloSydney Hong Kong Seoul Singapore Taipei Tokyo: Prentice Hall, 2018. ISBN: 978-0-13-449416-6.
[6] Microchip. 2014. URL: https://www.mouser.de/datasheet/2/268/20005167C-1512552.pdf(besucht am 26. 12. 2023).
[7] mikrocontroller.net. URL: https://www.mikrocontroller.net/attachment/6819/canbus.pdf(besucht am 27. 12. 2023).
