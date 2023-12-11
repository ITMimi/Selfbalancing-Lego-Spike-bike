# Selfbalancing-Lego-Spike-bike

Bei dem im folgenden vorgestellte Projekt handelt es sich um einen Prototyp eines selbstausbalancierenden Motorrads, das ausschließlich aus LEGO®-Bausteinen konstruiert und mit der LEGO®-Spike bzw LEGO®-Mindstorms App programmiert wurde. Die Idee war es, das eingebaute Gyroskop zu nutzen um zu registrieren, wenn das Motorrad in eine Richtung kippt (Änderungen im Roll-Winkel) und das Motorrad durch entsprechende Lenkbewegungen wieder aufzustellen. Außerdem wurde versucht eine Controller-Steuerung zu implementieren. 

Das Projekt ist inspiriert und orientiert sich an dem Self Balancing Bike von dem YouTube Kanal [Creator Academy Australia](https://www.youtube.com/watch?v=MCVW2Uqanlw).

# Bauanleitung

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

# Code

## Downloads:

[Code](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/blob/main/Code/Spike%20App/Selfbalancing_Bike_SpikeApp_final.llsp3) für Spike App

[Code](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/blob/main/Code/Mindstorms%20App/Selfbalancing_Bike_MindstormsApp_final.lms) für Mindstorms App

## Code Erklärung:

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
_17. setze Kh auf 0.26_
<br />

Hier werden die einzelnen Parameter initialisiert und es wird jeweils ein Wert zugewiesen. Die Parameter werden in der Schleife genutzt um die verschiedenen Variablen (Error, Derrivate, etc.) zu gewichten. Wir haben die besten Ergebnisse mit den hier angegebenen Werten erzielt. In der Balancing-Schleife gehen wir noch einmal genauer auf die Werte ein.  

__*Antrieb*__
<br />

_18. Motorpaar stelle Geschwindigkeit auf -85% ein_
<br />
_19. Motorpaar weise Bewegungsmotoren Anschlüsse E+F zu_
<br />
_20. Motorpaar starte Bewegung geradeaus:0_
<br />

Dieser Codeabschnitt verbindet die beiden Motoren, welche an den Anschlüssen E und F befestigt sind, zu einem Motorpaar. Die Gewschwindigkeit wird auf -85% gesetzt. Dabei ist es relevant zu beachten, mit welcher Ausrichtung die Motoren an dem Hinterrad befestigt sind. In unserem Setup mussten sich die Motoren nach "hinten" drehen, um das Motorrad nach vorne anzutreiben. Daher das Minus vor dem Geschwindigkeitswert. Wenn die beiden Motoren getauscht und auf die jeweils andere Seite des Rads montiert werden, muss auch das Vorzeichen geändert werden. 

__*Schleife*__
<br />

_21. wiederhole bis Betrag von Roll-Winkel > 70_
<br />
_22. setze Error auf Balance Target - Roll-Winkel_
<br />
_23. setze Integral auf Integral + Error * 0.25_
<br />
_24. setze Derrivate auf Error - previous error_
<br />
_25. setze previous error auf Error_
<br />
_26. setze Heading auf Heading Target - Gier-winkel_
<br />
_27. setze Result auf (Error * Kp) + (Integral * Ki) + (Derrivate * Kd)+ (Heading * Kh)_
<br />
_28. Motor B starte Motor mit Result * Steerpower % Leistung_
<br />

Kommen wir nun zum Herzstück des Codes. Diese Schleife nutzt die verschiedenen Variablen und Parameter um auf die Änderungen im Roll-Winkel des Motorrads zu reagieren und dieses durch Lenkbewegungen auszubalancieren. Dazu wird eine "while-Schleife" verwendet, die so lange geöffnet bleibt, bis der Betrag vom Roll-Winkel größer als 70 ist. Diese Grenze dient der Erkennung, ob das Motorrad umgefallen ist. Wenn also das Motorrad in eine Richtung weiter als 70 Grad kippt, endet die Schleife. Es ist wichtig den Betrag zu verwenden, da der Roll-Winkel in eine Kipprichtung ins Negative kleiner wird. In den nächsten Zeilen werden die verschiedenen Variablen berechnet. Zuerst wird der "Error"-Wert berechnet. Dieser ist das Balance-Target, welches auf 0 festgelegt ist minus dem aktuellen Roll-Winkel. 

__*Roboter Umgekippt*__
<br />

_29. Motorpaar halte an_
<br />
_30. Motor B stoppe Motor_
<br />
_31. Motor B gehe auf kürzestem Wege auf Position 0_
<br />

Wenn die Schleife beendet wurde, da der Betrag vom Roll-Winkel größer als 70 geworden ist, also das Motorrad umgekippt ist, werden sowohl der Antrieb, als auch der Motor für die Lenkung gestoppt. Außerdem wird das Vorderrad wieder in die Startposition 0 gebracht. 

## Unterschiede Spike-App und Mindstorms-App 

Grundsätzlich funktioniert der oben beschriebene Code sowohl in der Spike- als auch in der Mindstorms-App. Wir haben jedoch festgestellt, dass ein Wert angepasst werden muss. 

# Controller-Steuerung

## Downloads

[Code](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/blob/main/Code/Mindstorms%20App/Lego_Spike_Bike_ControllerSteuerung_MindstormsApp.lms) für Mindstorms App

## Code Erklärung


# Fazit  

## Ergebnis

In den beiden Videos ist das Selfbalancing-Lego-Spike-bike zu sehen. Sowohl auf dem Teppichboden, als auch auf dem etwas glatteren Bodenbelag ist das Motorrad in der Lage eingenständig zu fahren und sich durch Lenkbewegungen auszubalancieren. 

https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/assets/153182286/547acb4e-3f02-45bf-bd1d-e70390bd240c

https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/assets/153182286/27c758a2-e49b-49fe-b1d6-4038bd6fde2a

## Probleme in der Entwicklung

Wir haben zuerst eine andere, weniger kompakte, Bauweise für das Motorrad gewählt. Dadurch wird es jedoch deutlich schwieriger dieses auszubalancieren. Wir haben uns daher dazu entschieden uns an der Bauweise aus dem [YouTube-Video](https://www.youtube.com/watch?v=IiCZoNBiXc0) zu orientieren. Auch bei der programmierung haben wir uns an dem [Programmier-Tutorial](https://www.youtube.com/watch?v=TupLmKkHMBU&t=0s) von der [Creator Academy Australia](https://www.youtube.com/watch?v=MCVW2Uqanlw) orientiert. Dabei haben wir jedoch sehr schnell festgestellt, dass die in dem Video gewählten Parameter für unser Modell nicht funktionieren. Daher haben wir begonnen systematisch die verschiedenen Parameter zu variieren und die Veränderungen in der zurückgelegten Distanz zu messen. Dabei machten wir kaum messbare Fortschritte. Auffällig war, dass das Motorrad auch bei kleinen Kippwinkeln sehr stark gegengelenkt hat und dadurch noch schneller umgekippt ist. Wir haben daher den Parameter (Kp), welcher den Fehler-Wert (Error) gewichtet von 2 auf 1 halbiert. Danach war das Motorrad in der Lage sich selbst auszubalancieren. Die anderen Parameter spielen dabei zum Teil eine untergeordnete Rolle. 

__*Controller-Steuerung*__

Nachdem das Motorrad in der Lage war, sich selbst auszubalancieren, haben wir versucht eine Controller-Steuerung zu implementieren. Dabei sind wir leider auf verschiedene Probleme gestoßen, welche wir aus zeitlichen Gründen nicht mehr lösen konnten. Am entscheidensten war der Unterschied vom Download- zum Streaming-Modus. Während die Balancierung im Download-Modus, mit den oben gewählten Werten, problemlos funktioniert, ist das Motorrad im Streaming-Modus bei gleichem Code nicht mehr in der Lage zu fahren.  


