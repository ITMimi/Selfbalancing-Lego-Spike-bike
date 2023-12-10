# Selbalancing_Bike_SpikeApp Code Erklärung

Im Folgenden gehen wir durch jede Zeile des Codes und erklären diese. 
<br />

### Start des Prgramms 
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

### Initialisierung von Variablen und Parametern 

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

## Evtl. erläutern was es bei den Werten und Parametern auf sich hat.
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
