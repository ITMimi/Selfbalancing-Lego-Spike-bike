# Selfbalancing-Lego-Spike-bike

Bei dem im folgenden vorgestellte Projekt handelt es sich um einen Prototyp eines selbstausbalancierenden Motorrads, das ausschließlich aus LEGO®-Bausteinen konstruiert und mit der LEGO®-Spike bzw LEGO®-Mindstorms App programmiert wurde. Die Idee war es, das eingebaute Gyroskop zu nutzen um zu registrieren, wenn das Motorrad in eine Richtung kippt (Änderungen im Roll-Winkel) und das Motorrad durch entsprechende Lenkbewegungen wieder aufzustellen. Außerdem wurde versucht eine Controller-Steuerung zu implementieren. 

Das Projekt ist inspiriert und orientiert sich an dem Self Balancing Bike von dem YouTube Kanal [Creator Academy Australia](https://www.youtube.com/watch?v=MCVW2Uqanlw).

![Motorrad gerendert](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/assets/153182286/60a006b5-6999-48e9-98ae-e05d470d66ad)

# Inhaltsverzeichnis

|Inhalt|
|------|
| [1. Bauanleitung](#Bauanleitung)| 
|&nbsp;&nbsp;&nbsp;[1.1 Benötigte Bauteile](#Benötigte-Bauteile)
&nbsp;&nbsp;&nbsp;[1.2 Aufbauanleitung](#Aufbauanleitung)
&nbsp;&nbsp;&nbsp;[1.3 CAD-Modell](#CAD-Modell)|
|[2. Code](#Code)|
|&nbsp;&nbsp;&nbsp;[2.1 Downloads](#Downloads)
&nbsp;&nbsp;&nbsp;[2.2 Unterschiede Spike-App und Mindstorms-App](#Unterschiede-Spike-App-und-Mindstorms-App)
&nbsp;&nbsp;&nbsp;[2.3 Code Erklärung](#Code-Erklärung)|
|[3. Controller-Steuerung](#Controller-Steuerung)|
|&nbsp;&nbsp;&nbsp;[3.1 Downloads](#Downloads-1)
&nbsp;&nbsp;&nbsp;[3.2 Code Erklärung](#Code-Erklärung-1)|
|[4. Zusammenfassung](#Zusammenfassung)|
|&nbsp;&nbsp;&nbsp;[4.1 Ergebnis](#Ergebnis)
&nbsp;&nbsp;&nbsp;[4.2 Probleme in der Entwicklung](#Probleme-in-der-Entwicklung)|

# Bauanleitung

## Benötigte Bauteile

| Bauteil | Anzahl |                
|---------|--------|
| Lego Spike Hub (53444)   | 1      |  
| Großer Motor (54675)     | 1      |
| Kleiner Motor (54696) | 2      |
| Großes Rad (49295)   | 2      |
| 4x2 Baustein (Bunt) (39789)| 8     |
|16x2 Baustein Flach (Lila) (4282)| 2  |
| 8x2 Baustein Flach (Schwarz) (3738)  | 2  |
| 2x2 Baustein abgerundet (Schwarz) (44126)| 2|
| 3x1 Verbindungsschiene (Gelb) (32523)| 4 |
| 7x1 Verbindungsschiene (Blau) (32524)| 3 |
| 9x1 Verbindungsschiene (Schwarz) (40490)| 3 |
| gebogenes Panel (Blau) (11954)| 2|
| T - Verbindungsstück (Schwarz) (60484)| 2 |
| Kreuz - Verbindungsstück (Lila) (39793)| 4 |
| Kreuz - Verbindungsstück (Schwarz) (39793)| 1 |
| Verbindungsstange mittel (Gelb) (44294)| 1 |
| Verbindungsstange kurz (Gelb) (4519)| 3 |
| Verbindungsstück (Blau) (6558)| 4 |
| Verbindungsstück (Schwarz) (2780)| 50 |
| Verbindungsfixierung (Grau) (6590)| 2 |
| Kabelfixierung (Bunt)  (49283)| 3  |
| 2x2 Plättchen (Blau) (4032) | 4 |
| Plättchen (Schwarz) (15535)| 2 |

![Bauanleitung Roboter Bild](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/assets/153182286/72ea02f9-630d-45fe-be9d-5af9da3b8c80)

## Aufbauanleitung

![Motorrad_Lego_Spike_Anleitung](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/assets/153182286/47e7730f-5b3e-4616-881c-5f0ab07418a2)

__*Download:*__ [Bauanleitung](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/files/13789514/Lego_Spike_Motorrad_Bauanleitung.pdf)


## CAD-Modell

![Aufbauanleitung GIF (2)](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/assets/153182286/ac4b700d-944a-4121-8323-258da6c6a848)

Es gibt verschiedene Dateiformate für das CAD Modell des Balancing Bikes. 
Erstellt wurde das CAD Modell mit der kostenfreiens App: Studio 2.0 von BrickLink. ([Downloadlink](https://www.bricklink.com/v3/studio/download.page)) 
Dabei lässt sich das Modell mit der Datei mit der Endung .io am leichtesten importieren zum Anschauen und Auseinandernehmen. 
Nach dem Öffnen der App auf New Project klicken. Dann sollte der Bildschirm aussehen wie auf dem folgenden Bild. Dann auf den Reiter oben Links "File" -> "Open" klicken und dann die heruntergeladene CAD-Datei mit der Endung .io auswählen. 

__*Download:*__ [.dae](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/blob/main/Cad/CAD.dae) [.io](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/blob/main/Cad/CAD.io) [.lxfml](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/blob/main/Cad/CAD.lxfml) [.pov](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/blob/main/Cad/CAD.pov) [.xml](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/blob/main/Cad/CAD.xml)
</br></br>
<img width="953" alt="image" src="https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/assets/153181616/9e54e68c-6ba1-4490-859f-18de0af0ad80">

# Code

## Downloads

[Code](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/blob/main/Code/Spike%20App/Selfbalancing_Bike_SpikeApp_final.llsp3) für Spike App

[Code](https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/blob/main/Code/Mindstorms%20App/Selfbalancing_Bike_MindstormsApp_final.lms) für Mindstorms App

## Unterschiede Spike-App und Mindstorms-App 

Die erste Version des selbstausbalancierenden Motorrads haben wir in der Spike App erstellt. Um die Möglichkeit zu haben eine Controller-Steuerung zu implementieren sind wir dann auf die Mindstorms App umgestiegen und mussten dort ein paar Parameter anpassen (z.B. die Geschwindigkeitsleistung). Daher sind in beide Code-Versionen in den entsprechenden Ordnern zu finden. Der folgende Code funktioniert sowohl in der Spike-App als auch in der Mindstorms-App. Lediglich die Antriebsgeschwindigkeit wurde in der Mindstorms-App von 85% auf 100% erhöht.   

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

# Zusammenfassung

## Ergebnis

In den beiden Videos ist unser Prototyp des sich selbst ausbalancierenden Motorrads zu sehen. Das Motorrad ist in der Lage längere Strecken zurückzulegen und sich dabei durch Lenkbewegungen zu stabilisieren, welche mithilfe des Gyroskosps berechnet werden. Getestet haben wir den Mechanismus auf Teppichboden (Video 2) und auf dem glatteren Gummibodenbelag (Video 1). Auf beiden Untergründen war das Motorrad in der Lage sich selbst auszubalancieren. Außerdem haben wir eine erste Idee für eine Controller-Steuerung entwickelt. 

https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/assets/153182286/547acb4e-3f02-45bf-bd1d-e70390bd240c

https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/assets/153182286/27c758a2-e49b-49fe-b1d6-4038bd6fde2a

## Probleme in der Entwicklung

### Bauweise
Wir haben zuerst eine andere, weniger kompakte, Bauweise für das Motorrad gewählt. Uns ist relativ schnell aufgefallen, dass es dadurch wesentlich schwieriger wurde das Motorrad auszubalancieren. Wir haben uns daher dazu entschieden uns an der Bauweise aus dem [YouTube-Video](https://www.youtube.com/watch?v=IiCZoNBiXc0) zu orientieren. 

### Programmierung

Auch bei der Programmierung haben wir uns an dem [Programmier-Tutorial](https://www.youtube.com/watch?v=TupLmKkHMBU&t=0s) von der [Creator Academy Australia](https://www.youtube.com/watch?v=MCVW2Uqanlw) orientiert. Dabei sind wir auf verschiedene Probleme gestoßen. Im ersten Schritt haben wir den Code übernommen und geschaut, ob das Motorrad direkt in der Lage ist sich selbst auszubalancieren. Das war nicht der Fall. Das Motorrad ist in fast allen Testläufen nach wenigen Zentimetern umgekippt. Es gab einzelne Testläufe in denen das Motorrad in der Lage war wenige Meter zu fahren, was jedoch lediglich daran lag, dass das Motorrad in jenen Testläufen sehr lange aufrecht blieb und daher keine Lenkbewegungen notwendig waren. Es wurde recht deutlich, dass die Lenkbewgungen zu stark und zu ruckartig ausgeführt wurden. Daher haben wir versucht die Parameter (Kh, Kd, etc.) systematisch zu variieren und geschaut, bei welchen Veränderung die Stabilität des Motorrads erhöht wurde. Wir versuchten dabei die Parameter so anzupassen, dass die Lenkbewegungen sanfter durchgeführt werden. Wir konnten beobachten, dass die zurückgelegte Strecke größer wurde, wenn wir den Parameter "Kp", welcher den Fehler gewichtet, kleiner gemacht haben. Nach einigen Versuchen stellten wir fest, dass eine Halbierung des "Kp"-Wertes von 2 auf 1 unser Problem löste und für die beste Stabilität sorgte. Die anderen Parameter beließen wir bei den Werten aus dem [Video](https://www.youtube.com/watch?v=TupLmKkHMBU&t=0s), wir stellten jedoch fest, dass das Motorrad auch ohne die Variable "Integral" in der Lage war zu fahren. 

Im Laufe des Tests stellten wir außerdem fest, dass die Variablen nach Beendigung des Programms nicht zurückgesetzt wurden, was zu Fehlern in der Berechnung der Lenkbewegungen führte. Wir lösten das Problem, wie bereits in der [Code-Erklärung](#Initialisierung-von-Variablen-und-Parametern) beschrieben, in dem alle Variablen im Code manuell zurückgesetzt werden.   

### Controller-Steuerung

Nachdem das Motorrad in der Lage war, sich selbst auszubalancieren, haben wir versucht eine Controller-Steuerung zu implementieren. Dabei sind wir leider auf verschiedene Probleme gestoßen, welche wir aus zeitlichen Gründen nicht mehr lösen konnten. Am entscheidensten war der Unterschied vom Download- zum Streaming-Modus. Der Streaming-Modus ist notwendig, um die Controller-Inputs registrieren und verarbeiten zu können. Während die Balancierung im Download-Modus, problemlos funktioniert, ist das Motorrad im Streaming-Modus bei gleichem Code nicht mehr in der Lage zu stabil fahren.  

### Connection zwischen Hub und Computer

Troubleshooting nicht Connecten des Hubs in der Mindstorm App: Es ist anzumerken, dass es beim Bluetooth-Verbinden des aktualsierten Hubs (grün leuchtender Ring) Schwierigkeiten in der Mindstorms App gab. Daher mussten wir den Hub Downgraden -> Siehe link https://spikelegacy.legoeducation.com/hubdowngrade/#step-1 , um ihn dann in der Mindstorms App zu verbinden und dort erneut zu aktualisieren. Danach funktionierte des Bluetooth-Verbinden in der Spike und Mindstorm App problemlos.

# Quellen

## Videos von [Creator Academy Australia](https://www.youtube.com/@CreatorAcademyAustralia)

[Vorstellungsvideo](https://www.youtube.com/watch?v=MCVW2Uqanlw)

[Programmier-Tutorial](https://www.youtube.com/watch?v=TupLmKkHMBU)

[Aufbauanleitung](https://www.youtube.com/watch?v=IiCZoNBiXc0)
