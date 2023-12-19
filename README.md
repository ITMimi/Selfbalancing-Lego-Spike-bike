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

Für die Programmierung des Motorrads haben wir den Textblockmodus der Spike- bzw. Mindstorms-App verwendet. Im Folgenden gehen wir durch die verschiedenen Abschnitte des Codes und erklären diese. Die einzelnen Textbausteine sind entsprechend durchnummeriert.  

__*Start des Prgramms*__
<br />

     1. wenn Programm startet
     2. Motor B gehe auf kürzestem Wege auf Position 0
     3. warte 1 Sekunden

 Nach dem Start des Programms wird als erstes das Vorderrad nach vorne ausgerichtet und so in die Startposition (Position 0) gebracht. Danach wartet das Programm für eine Sekunde und fährt dann fort.

__*Initialisierung von Variablen und Parametern*__ 

     4. setze Gierwinkel auf 0

An dieser Stelle wird der Gierwinkel des Gyroskops mit dem Wert 0 initialisiert. In den späteren Berechnungen wird die Abweichung der Ausrichtung ("Heading") während der Fahrt von der Ausrichtung zum Fahrtbeginn verwendet (s.Z. 26), um eine möglichst gerade Fahrt zu ermöglichen. Dazu ist es notwendig, dass der Zielwert der Ausrichtung ("Heading Target") der Ausrichtung zum Beginn entspricht. Wir haben uns dazu entschieden das "Heading Target" auf 0 (s.Z. 6) zu setzen und müssen daher den Gierwinkel zu Beginn dementsprechend initialisieren. Eine Alternative wäre es das "Heading Target" auf den Anfangswert des Gierwinkels zu setzen.

     Alt.: setze Heading Target auf Gierwinkel

Für den Roll-Winkel gilt gegenteiliges. Hier ist nicht die Abweichung von der Startposition sondern zum "absoluten" Wert relevant. Damit das Motorrad stabil bleibt, müssen durch die Startposition verursachte Abweichungen direkt berücksichtigt und ausgeglichen werden.      

     5. setze Balance Target auf 0
     6. setze Heading Target auf 0

Die Zielwerte für die Ausrichtung ("Heading Target"), sowie für den Roll-Winkel ("Balance Target") werden auf 0 gesetzt.
     
     7. setzte Result auf 0
     8. setze Heading auf 0
     9. setze Error auf 0
     10. setze Derrivate auf 0
     11. setze previous error auf 0     
     12. setze Integral auf 0

In diesem Abschnitt werden die Variablen, welche für die Lenkbewegungen benötigt werden deklariert und auf 0 gesetzt. Prinzipiell sollte es nicht notwendig sein, die Variablen bereits an dieser Stelle zu initialisieren. Wir sind jedoch in der Testphase auf das Problem gestoßen, dass einzelne Variablen nicht korrekt zurückgesetzt wurden, wenn das Programm neu gestartet wurde. Daher werden alle Variablen an dieser Stelle einmal auf 0 gesetzt. 

     13. setzte Steerpower auf 2.6
     14. setze Kp auf 1
     15. setze Ki auf 0.02
     16. setze Kd auf 18
     17. setze Kh auf 0.26

Hier werden die verschiedenen Parameter, mit denen die Variablen in der Balancing-Schleife (s.Z. 21) gewichtet werden, initialisiert. Wir haben die besten Ergebnisse mit den hier angegebenen Werten erzielt. In der Balancing-Schleife gehen wir noch einmal genauer auf die Werte ein.  

__*Antrieb*__

     18. Motorpaar stelle Geschwindigkeit auf -85% ein
     19. Motorpaar weise Bewegungsmotoren Anschlüsse E+F zu
     20. Motorpaar starte Bewegung geradeaus: 0

Dieser Codeabschnitt verbindet die beiden (Antriebs-)Motoren, welche an den Anschlüssen E und F befestigt sind, zu einem Motorpaar. Die Gewschwindigkeit wird auf -85% gesetzt. Dabei ist es relevant zu beachten, mit welcher Ausrichtung die Motoren an dem Hinterrad befestigt sind. In unserem Setup mussten sich die Motoren nach "hinten" drehen, um das Motorrad nach vorne anzutreiben. Daher das Minus vor dem Geschwindigkeitswert. Wenn die beiden Motoren getauscht und auf die jeweils andere Seite des Rads montiert werden, muss auch das Vorzeichen geändert werden. 

__*Schleife*__

     21. wiederhole bis Betrag von Roll-Winkel > 70

Kommen wir nun zum Herzstück des Codes. Diese Schleife nutzt die verschiedenen Variablen und Parameter um auf die Änderungen im Roll-Winkel des Motorrads zu reagieren und dieses durch Lenkbewegungen auszubalancieren. Dazu wird eine "while-Schleife" verwendet, die so lange geöffnet bleibt, bis der Betrag vom Roll-Winkel größer als 70 ist. Diese Grenze dient der Erkennung, ob das Motorrad umgefallen ist. Wenn also das Motorrad in eine Richtung weiter als 70 Grad kippt, endet die Schleife. Wichtig ist es dabei den Betrag zu verwenden, da der Roll-Winkel in eine Kipprichtung ins Negative kleiner wird. 

     22. setze Error auf Balance Target - Roll-Winkel 

Zuerst wird der "Error"-Wert, also die Abweichung des Roll-Winkels zum Zielwert (Balance Target, 0), berechnet.

     23. setze Integral auf Integral + Error * 0.25

Das Integral bildet die Tendenz ab, in welche das Motorrad häufiger kippt. Der Wert ergibt sich durch die Addition des vorherigen Werts mit dem Error-Wert, welcher mit dem Faktor 0.25 gewichtet wird. Da der Error Wert je nach Kipprichtung positiv oder negativ ist, gleicht sich das Integral aus und sollte sich im Optimalfall um 0 herum bewegen. Kippt das Motorrad jedoch häufiger in eine Richtung wird der Wert dementsprechen größer oder kleiner (negativ) und sorgt so dafür, dass die Ausgleichsbewegungen in die eine Richtung verstärkt und in die andere Richtung abgeschwächt werden. 

     24. setze Derrivate auf Error - previous error
     25. setze previous error auf Error

__Neu formulieren, nur damit ich mir den grundsätzlichen Sinn merke__ In der Variable "Derrivate" wird der vorherige Fehler berücksichtigt. Wenn das Motorrad durch die Vorherige Ausgleichsbewegung zu stark in die andere Richtung kippt wird auch die darauf folgende Ausgleichsbewegung stärker um das ganze so auszugleichem. Im Optimalfall ist die Differenz zwischen aktuellem und vorherigen Fehler möglichst klein, da dies bedeutet, dass die Ausgleichsbewegungen sehr sanft sind. 

     26. setze Heading auf Heading Target - Gier-winkel

__Neu formulieren, nur damit ich mir den grundsätzlichen Sinn merke__ Die Variable Heading soll dafür sorgen, dass das Motorrad möglichst auf einer geraden  Linie fährt und berücksichtigt daher noch den Gier-Winkel, also der Winkel, welcher sich verändert, wenn sich das Motorrad nach links oder rechts ausrichtet. 
      
     27. setze Result auf (Error * Kp) + (Integral * Ki) + (Derrivate * Kd)+ (Heading * Kh)    
     28. Motor B starte Motor mit Result * Steerpower % Leistung

In der Zeile 27 werden diese Variablen dann mit den vorher festgelegten Parametern gewichtet und addiert. Deutlich wird, dass vor allem die Variable "Derrvivate" und "Error" dabei eine große Rolle spielen. Die Stabilität des Motorrads wird vom Integral und dem Heading kaum beeinflusst. Wir haben zum Test die Variable Integral rausgenommen und das Motorrad war dennoch in der Lage sich selbst auszubalancieren. Jedoch funktionierte es etwas sanfter, wenn die Variable behalten wird. 

Am Ende wird der Motor, welcher für die Lenkung genutzt wird und bei uns am Anschluss B angeschlossen wurde mit der entsprechenden Leistung gestartet. Die Lenkrichtung wird dabei durch das Vorzeichen des Wertes "Result" bestimmt.

__*Roboter Umgekippt*__

     29. Motorpaar halte an
     30. Motor B stoppe Motor
     31. Motor B gehe auf kürzestem Wege auf Position 0

Dieser Teil des Codes wird nur erreicht, wenn die Schleife beendet wurde, also das Motorrad umgekippt ist. Das Antriebsmotorpaar wird dann gestoppt, und das Vorderrad wieder in die Anfangsposition gedreht.  

## Unterschiede Spike-App und Mindstorms-App 

Der oben beschriebene Code funktioniert sowohl in der Spike-App als auch in der Mindstorms-App. Lediglich die Geschwindigkeit des Antriebs wurde von 85% auf 100% erhöht.   

# Controller-Steuerung

## Downloads

[Code](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/blob/main/Code/Mindstorms%20App/Lego_Spike_Bike_ControllerSteuerung_MindstormsApp.lms) für Mindstorms App

## Code Erklärung

Leider hat die Steuerungsumsetzung schlussendlich nicht funktioniert, dennoch wollen wir unseren Versuchscode nicht vorenthalten
und den Steuerungscode teilen. 
Es ist zu beachten, dass das Programm im "streaming mode" gestartet werden muss, wenn man eine Steuerung nutzt.
'Bild einfügen'

     1. wenn das Programm startet
     2. B auf kürzestem Wege auf 0 bringen
     3. warte 1 Sekunde

blabla

     4. setze Geschwindigkeit auf -100

blabla

     5. Antriebsmotoren Anschluss E+F zuweisen

blabla

     6. wiederhole fortlaufend
     7. Motorpaar nach geradeaus: 0 mit Geschwindigkeit & Geschwindigkeit starten
     8. B relative Position Controller links Joystick X-Achse mit einer Geschwindigkeit von 80% einnehmen

blabla

     9. Controller wenn R2 gedrückt wird 
     10. setze Geschwindigkeit auf Geschwindigkeit + 10
     11. Controller wenn L2 gedrückt wird
     12. setze Geschwindigkeit auf Geschwindigkeit - 10

blabla

     13. Controller wenn Kreis gedrückt wird
     14. Soundeffekt Kick abspielen
     15. schalte alle ab

blabla

# Zusammenfassung

## Ergebnis

In den beiden Videos ist das Selfbalancing-Lego-Spike-bike zu sehen. Sowohl auf dem Teppichboden, als auch auf dem etwas glatteren Bodenbelag ist das Motorrad in der Lage eingenständig zu fahren und sich durch Lenkbewegungen auszubalancieren. 

https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/assets/153182286/547acb4e-3f02-45bf-bd1d-e70390bd240c

https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/assets/153182286/27c758a2-e49b-49fe-b1d6-4038bd6fde2a

## Probleme in der Entwicklung

Wir haben zuerst eine andere, weniger kompakte, Bauweise für das Motorrad gewählt. Dadurch wird es jedoch deutlich schwieriger dieses auszubalancieren. Wir haben uns daher dazu entschieden uns an der Bauweise aus dem [YouTube-Video](https://www.youtube.com/watch?v=IiCZoNBiXc0) zu orientieren. Auch bei der programmierung haben wir uns an dem [Programmier-Tutorial](https://www.youtube.com/watch?v=TupLmKkHMBU&t=0s) von der [Creator Academy Australia](https://www.youtube.com/watch?v=MCVW2Uqanlw) orientiert. Dabei haben wir jedoch sehr schnell festgestellt, dass die in dem Video gewählten Parameter für unser Modell nicht funktionieren. Daher haben wir begonnen systematisch die verschiedenen Parameter zu variieren und die Veränderungen in der zurückgelegten Distanz zu messen. Dabei machten wir kaum messbare Fortschritte. Auffällig war, dass das Motorrad auch bei kleinen Kippwinkeln sehr stark gegengelenkt hat und dadurch noch schneller umgekippt ist. Wir haben daher den Parameter (Kp), welcher den Fehler-Wert (Error) gewichtet von 2 auf 1 halbiert. Danach war das Motorrad in der Lage sich selbst auszubalancieren. Die anderen Parameter spielen dabei zum Teil eine untergeordnete Rolle. 

__*Controller-Steuerung*__

Nachdem das Motorrad in der Lage war, sich selbst auszubalancieren, haben wir versucht eine Controller-Steuerung zu implementieren. Dabei sind wir leider auf verschiedene Probleme gestoßen, welche wir aus zeitlichen Gründen nicht mehr lösen konnten. Am entscheidensten war der Unterschied vom Download- zum Streaming-Modus. Während die Balancierung im Download-Modus, mit den oben gewählten Werten, problemlos funktioniert, ist das Motorrad im Streaming-Modus bei gleichem Code nicht mehr in der Lage zu fahren.  


