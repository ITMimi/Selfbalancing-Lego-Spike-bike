# Controller-Steuerung

## Downloads

[Code](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/blob/main/Code/Mindstorms%20App/Lego_Spike_Bike_ControllerSteuerung_MindstormsApp.lms) für Mindstorms App

## Code Erklärung 

Leider hat die Steuerungsumsetzung schlussendlich nicht funktioniert. Auf die Probleme gehen wir in der Zusammenfassung näher ein. Dennoch wollen wir unseren Versuchscode nicht vorenthalten
und den Steuerungscode teilen. Genutzt wurde ein Playstation 4 Controller. Es ist zu beachten, dass das Programm im "streaming mode" gestartet werden muss, wenn man eine Steuerung nutzt. Der Download-Modus ist der Standardmodus zum Ausführen von Programmen. Das Programm wird dabei zunächst auf dem Hub gespeichert und dann ausgeführt. Im Streaming-Modus werden die Programme in Echtzeit ausgeführt. Dadurch können noch Änderungen an den Programmparametern vorgenommen werden, während das Programm läuft. So können die Controller-Inputs registriert und berücksichtigt werden. 

| Download | Streaming |
|----------|-----------|
| ![Streaming_Download-Modus](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/assets/153182286/c1b60ce2-d6b6-49c4-913d-a3b10afbdc25) | ![Streaming_Modus](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/assets/153182286/59423d84-d9b5-4b0d-aa2f-572ab69415d5) |

### Start des Prgramms

     1. wenn das Programm startet
     2. B auf kürzestem Wege auf 0 bringen
     3. warte 1 Sekunde

Genauso wie im Code oben, wird als erstes das Vorderrad nach vorne (Position 0) ausgerichtet. Daraufhin wartet das Programm eine Sekunde bevor es fortfährt.

     4. setze Geschwindigkeit auf -100

Die Anfangsgeschwindigkeit wird auf (-)100 gesetzt. Auch hier muss die Ausrichtung der Antriebsmotoren berücksichtigen und das Vorzeichen ggf. anpassen.

     5. Antriebsmotoren Anschluss E+F zuweisen

Dem Antriebsmotorpaar werden die Anschlüsse E und F zugewiesen.

### Schleife

     6. wiederhole fortlaufend
     7. Motorpaar nach geradeaus: 0 mit Geschwindigkeit % Geschwindigkeit starten
     8. Motor B relative Position Controller links Joystick X-Achse mit einer Geschwindigkeit von 80% einnehmen

In einer durchgängig offenen Schleife wird immer wieder das Antriebsmotorpaar mit der entsprechenden Geschwindigkeit gestartet. Da die Geschwindigkeit durch das Drücken von Knöpfen auf dem Controller verändert werden kann, muss die Geschwindigkeit in der Schleife immer wieder neu abgefragt werden. Außerdem wird das Vorderrad durch den Motor B in die Position gedreht, welche der X-Achse des linken Joysticks entspricht. Dadurch ist es möglich das Motorrad mit dem Joystick zu lenken (siehe Video). 

### Geschwindigkeits-Steuerung

     9. Controller wenn R2 gedrückt wird 
     10. setze Geschwindigkeit auf Geschwindigkeit + 10
     11. Controller wenn L2 gedrückt wird
     12. setze Geschwindigkeit auf Geschwindigkeit - 10

An dieser Stelle wird die Geschwindigkeitskontrolle implementiert. Wenn der Benutzer den Knopf R2 auf dem Controller betätigt, wird die Geschwindigkeit um 10% erhöht. Wird die Taste L2 betätigt, wird die Geschwindigkeit um 10% reduziert. 

     13. Controller wenn Kreis gedrückt wird
     14. Soundeffekt Kick abspielen
     15. schalte alle ab

Durch das Betätigen der Kreis-Taste auf dem Controller werden alle Motoren ausgeschaltet. 

https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/assets/153182286/1c764151-db78-48aa-8c01-96dcab006854
