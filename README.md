# Selfbalancing-Lego-Spike-bike

Bei dem im folgenden vorgestellte Projekt handelt es sich um einen Prototyp eines selbstausbalancierenden Motorrads, das ausschließlich aus LEGO®-Bausteinen konstruiert und mit der LEGO®-Spike bzw LEGO®-Mindstorms App programmiert wurde. Die Idee war es, das eingebaute Gyroskop zu nutzen um zu registrieren, wenn das Motorrad in eine Richtung kippt (Änderungen im Roll-Winkel) und das Motorrad durch entsprechende Lenkbewegungen wieder aufzustellen. Außerdem wurde versucht eine Controller-Steuerung zu implementieren. 

Das Projekt ist inspiriert und orientiert sich an dem Self Balancing Bike von dem YouTube Kanal [Creator Academy Australia](https://www.youtube.com/watch?v=MCVW2Uqanlw).

## Bauanleitung

| Bauteil | Anzahl |                
|---------|--------|
| Lego Spike Hub   | 1      |  
| Großer Motor     | 1      |
| Kleiner Motor    | 2      |
| Großes Rad      | 2      |
| 4x2 Baustein (Bunt) | 8     |
|16x2 Baustein Flach (Lila) | 2  |
| 8x2 Baustein Flach (Schwarz)   | 2  |
| 2x2 Baustein abgerundet (Schwarz) | 2|
| 3x1 Verbindungsschiene (Gelb) | 4 |
| 7x1 Verbindungsschiene (Blau) | 3 |
| 9x1 Verbindungsschiene (Schwarz) | 3 |
| T - Verbindungsstück (Schwarz) | 2 |
| Kreuz - Verbindungsstück (Lila) | 4 |
| Kreuz - Verbindungsstück (Schwarz) | 1 |
| Verbindungsstange mittel (Gelb) | 1 |
| Verbindungsstange kurz (Gelb) | 3 |
| Verbindungsstück (Blau) | 4 |
| Verbindungsstück (Schwarz) | 50 |
| Verbindungsfixierung (Grau) | 2 |
| Kabelfixierung (Bunt)  | 3  |
| 2x2 Plättchen (Blau)  | 4 |
| Plättchen (Schwarz) | 2 |


![alt Text](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/blob/main/Images/Bauanleitung%20Roboter%20Bild.jpg)

Hier CAD einfügen. 

![Lego Spike Bike](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/assets/153182286/38a3e8bf-6ff8-4f24-8b36-1140f6adbaec)

[Aufbauanleitung](https://www.youtube.com/watch?v=IiCZoNBiXc0) von [Creator Academy Australia](https://www.youtube.com/watch?v=MCVW2Uqanlw).

## Code

### Downloads:

[Code](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/blob/main/Code/Spike%20App/Selfbalancing_Bike_SpikeApp_final.llsp3) für Spike App

[Code](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/blob/main/Code/Mindstorms%20App/Selfbalancing_Bike_MindstormsApp_final.lms) für Mindstorms App

### Code Erklärung:

Im Folgenden gehen wir durch jede Zeile des Codes und erklären diese. 
<br />

__*Start des Prgramms*__
<br />

_1. Wenn Programm startet_
<br />
_2. Motor B gehe auf kürzestem Wege auf Position 0_
<br />
_3. warte 1 Sekunden_
<br />

Wird das Programm gestartet, wird das Vorderrad gerade (auf Position 0) gestellt. Anschließend wird 1 Sekunde gewartet, bevor das Programm fortfährt. 
<br />

_4. setze Gierwinkel auf 0_
<br />

Der Gierwinkel wird in der Startposition auf 0 gesetzt. Dadurch werden Abweichungen im Roll-Winkel, welche durch die Startposition verursacht werden ausgeglichen.

__*Initialisierung von Variablen und Parametern*__ 

_5. setzte Result auf 0_
<br />
_6. setze Heading auf 0_
<br />
_7. setze Balance Target auf 0_
<br />
_8. setze Heading Target auf 0_
<br />
_9. setze Error auf 0_
<br />
_10. setze Derrivate auf 0_
<br />
_11. setze previous error auf 0_
<br />
_12. setze Integral auf 0_
<br />

In diesem Abschnitt werden die Variablen, welche für die Lenkbewegungen benötigt werden initialisiert und auf 0 gesetzt. Prinzipiell sollte das nicht notwendig sein, jedoch sind wir in der Testphase auf das Problem gestoßen, dass die Variablen nicht beim erneuten ausführen des Programms zurückgesetzt wurde, was zu Fehlern geführt hat. 

_13. setzte Steerpower auf 2.6_
<br />
_14. setze Kp auf 1_
<br />
_15. setze Ki auf 0.02_
<br />
_16. setze Kd auf 18_
<br />
_16. setze Kh auf 0.26_
<br />

## Fazit  

https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/assets/153182286/547acb4e-3f02-45bf-bd1d-e70390bd240c

https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/assets/153182286/27c758a2-e49b-49fe-b1d6-4038bd6fde2a



