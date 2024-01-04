# Code

## Downloads

[Code](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/blob/main/Code/Spike%20App/Selfbalancing_Bike_SpikeApp_final.llsp3) für [Spike-App](https://education.lego.com/de-de/downloads/spike-app/software/) (Geeignet ausschließlich für die Balancierung des Bikes)

[Code](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/blob/main/Code/Mindstorms%20App/Selfbalancing_Bike_MindstormsApp_final.lms) für [Mindstorms-App](https://education.lego.com/de-de/downloads/mindstorms-ev3/software/) (Geeignet wenn neben Selbstbalancierung, eine Steuerung geplant ist)

## Unterschiede Spike-App und Mindstorms-App 

Die erste Version des selbstausbalancierenden Motorrads haben wir in der Spike-App erstellt. Um die Möglichkeit zu haben eine Controller-Steuerung zu implementieren sind wir dann auf die Mindstorms-App umgestiegen und mussten dort ein paar Parameter anpassen (z.B. die Geschwindigkeitsleistung). Daher sind in beide Code-Versionen in den entsprechenden Ordnern zu finden. Der folgende Code funktioniert sowohl in der Spike-App als auch in der Mindstorms-App. Lediglich die Antriebsgeschwindigkeit wurde in der Mindstorms-App von 85% auf 100% erhöht.   

## Code Erklärung

Für die Programmierung des Motorrads haben wir den Textblockmodus der Spike- bzw. Mindstorms-App verwendet. Im Folgenden gehen wir durch die verschiedenen Abschnitte des Codes und erklären diese. Die einzelnen Textbausteine sind entsprechend durchnummeriert.  Es empfiehlt sich im Split-Screen-View die Erklärungen neben den Code zu legen.

#### Start des Programms

     1. wenn Programm startet
     2. Motor B gehe auf kürzestem Wege auf Position 0
     3. warte 1 Sekunden

 Nach dem Start des Programms wird als erstes das Vorderrad nach vorne ausgerichtet und so in die Startposition (Position 0) gebracht. Danach wartet das Programm für eine Sekunde und fährt dann fort.

### Initialisierung von Variablen und Parametern 

     4. setze Gierwinkel auf 0

An dieser Stelle wird der Gierwinkel des Gyroskops mit dem Wert 0 initialisiert. In den späteren Berechnungen wird die Abweichung der Ausrichtung ("Heading") während der Fahrt von der Ausrichtung zum Fahrtbeginn verwendet (siehe Zeile 26), um eine möglichst gerade Fahrt zu ermöglichen. Dazu ist es notwendig, dass der Zielwert der Ausrichtung ("Heading Target") der Ausrichtung zum Beginn entspricht. Wir haben uns dazu entschieden das "Heading Target" auf 0 (siehe Zeile 6) zu setzen und müssen daher den Gierwinkel zu Beginn dementsprechend initialisieren. Eine Alternative wäre es das "Heading Target" auf den Anfangswert des Gierwinkels zu setzen.

     Alt.: setze Heading Target auf Gierwinkel

Für den Roll-Winkel gilt gegenteiliges. Hier ist nicht die Abweichung von der Startposition sondern zum "absoluten" Wert relevant. Damit das Motorrad stabil bleibt, müssen durch die Startposition verursachte Abweichungen direkt berücksichtigt und ausgeglichen werden.      

     5. setze Balance Target auf 0
     6. setze Heading Target auf 0

Die Zielwerte für die Ausrichtung ("Heading Target"), sowie für den Roll-Winkel ("Balance Target") werden auf 0 gesetzt.

<a name="Reset"></a>

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

Hier werden die verschiedenen Parameter, mit denen die Variablen in der Balancing-Schleife (siehe Zeile 27) gewichtet werden, initialisiert. Wir haben die besten Ergebnisse mit den hier angegebenen Werten erzielt. 

### Antrieb

     18. Motorpaar stelle Geschwindigkeit auf -85% ein
     19. Motorpaar weise Bewegungsmotoren Anschlüsse E+F zu
     20. Motorpaar starte Bewegung geradeaus: 0

Dieser Codeabschnitt verbindet die beiden (Antriebs-)Motoren, welche an den Anschlüssen E und F befestigt sind, zu einem Motorpaar. Die Gewschwindigkeit wird auf -85% gesetzt. Dabei ist es relevant zu beachten, mit welcher Ausrichtung die Motoren an dem Hinterrad befestigt sind. In unserem Setup mussten sich die Motoren nach "hinten" drehen, um das Motorrad nach vorne anzutreiben. Daher das Minus vor dem Geschwindigkeitswert. Wenn die beiden Motoren getauscht und auf die jeweils andere Seite des Rads montiert werden, muss auch das Vorzeichen geändert werden. 

### Schleife

     21. wiederhole bis Betrag von Roll-Winkel > 70

Kommen wir nun zum Herzstück des Codes. Diese Schleife nutzt die verschiedenen Variablen und Parameter um auf die Änderungen im Roll-Winkel des Motorrads zu reagieren und dieses durch Lenkbewegungen auszubalancieren. Dazu wird eine "while-Schleife" verwendet, die so lange geöffnet bleibt, bis der Betrag vom Roll-Winkel größer als 70 ist. Diese Grenze dient der Erkennung, ob das Motorrad umgefallen ist. Wenn also das Motorrad in eine Richtung weiter als 70 Grad kippt, endet die Schleife. Wichtig ist es dabei den Betrag zu verwenden, da der Roll-Winkel in eine Kipprichtung ins Negative kleiner wird. 

     22. setze Error auf Balance Target - Roll-Winkel 

Zuerst wird der "Error"-Wert, also die Abweichung des Roll-Winkels zum Zielwert (Balance Target, 0), berechnet.

     23. setze Integral auf Integral + Error * 0.25

Das "Integral" bildet die Tendenz ab, in welche das Motorrad häufiger kippt. Der Wert ergibt sich durch die Addition des vorherigen Werts mit dem "Error"-Wert, welcher mit dem Faktor 0.25 gewichtet wird. Da der "Error" Wert je nach Kipprichtung positiv oder negativ ist, gleicht sich das "Integral" aus und sollte sich im Optimalfall um 0 herum bewegen. Kippt das Motorrad jedoch häufiger in eine Richtung wird der Wert dementsprechen größer oder kleiner (negativ) und sorgt so dafür, dass die Ausgleichsbewegungen in die eine Richtung verstärkt und in die andere Richtung abgeschwächt werden. 

     24. setze Derrivate auf Error - previous error
     25. setze previous error auf Error

In der Variable "Derrivate" wird die Differenz zwischen aktuellem und vorherigem Fehler berechnet. Ist der Drehimpuls des Motorrads sehr hoch, d.h. das Motorrad kippt sehr schnell in eine Richtung, wird der Wert größer, bzw. ins negative kleiner. Die Ausgleichsbewegungen werden dementsprechend schneller durchgeführt. Im Optimalfall nähert sich der Wert langsam der 0, da dies bedeutet, dass das Motorrad sehr stabil aufrecht fährt und nur sanfte Lenkbewegungen notwendig sind.

     26. setze Heading auf Heading Target - Gier-winkel

Die Variable Heading berücksichtigt die Ausrichtung des Motorrads und soll dafür sorgen, dass das Motorrad möglichst auf einer geraden Linie fährt. Dazu wird die Abweichung der aktuellen Ausrichtung von der Ausrichter zum Fahrtbeginn berechnet. 
      
     27. setze Result auf (Error * Kp) + (Integral * Ki) + (Derrivate * Kd)+ (Heading * Kh)    
     28. Motor B starte Motor mit Result * Steerpower % Leistung

In der Zeile 27 werden diese Variablen dann mit den vorher festgelegten Parametern gewichtet und addiert. Deutlich wird, dass vor allem die Variable "Derrvivate" und "Error" dabei eine große Rolle spielen. Die Stabilität des Motorrads wird vom Integral und dem Heading kaum beeinflusst. Auch ohne die Variable "Integral" war das Motorrad in der Lage sich selbst auszubalancieren. Die besten Ergebnisse erzielten wir jedoch, wenn alle Variablen mit einbezogen wurden. 

Am Ende wird der Motor, welcher für die Lenkung genutzt wird und bei uns am Anschluss B angeschlossen wurde mit der entsprechenden Leistung gestartet. Die Lenkrichtung wird dabei durch das Vorzeichen des Wertes "Result" bestimmt.

### Roboter Umgekippt

     29. Motorpaar halte an
     30. Motor B stoppe Motor
     31. Motor B gehe auf kürzestem Wege auf Position 0

Dieser Teil des Codes wird nur erreicht, wenn die Schleife beendet wurde, also das Motorrad umgekippt ist. Das Antriebsmotorpaar wird dann gestoppt, und das Vorderrad wieder in die Anfangsposition gedreht.
