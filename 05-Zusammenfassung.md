# Zusammenfassung

## Ergebnis

In den beiden Videos ist unser Prototyp des sich selbst ausbalancierenden Motorrads zu sehen. Das Motorrad ist in der Lage längere Strecken zurückzulegen und sich dabei durch Lenkbewegungen zu stabilisieren, welche mithilfe des Gyroskosps berechnet werden. Getestet haben wir den Mechanismus auf Teppichboden (Video 2) und auf dem glatteren Gummibodenbelag (Video 1). Auf beiden Untergründen war das Motorrad in der Lage sich selbst auszubalancieren. Außerdem haben wir eine erste Idee für eine Controller-Steuerung entwickelt. 

https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/assets/153182286/547acb4e-3f02-45bf-bd1d-e70390bd240c

https://github.com/ITMimi/Selfbalancing-Lego-Spike-bike/assets/153182286/27c758a2-e49b-49fe-b1d6-4038bd6fde2a

## Probleme in der Entwicklung

### Bauweise
Wir haben zuerst eine andere, weniger kompakte, Bauweise für das Motorrad gewählt. Uns ist relativ schnell aufgefallen, dass es dadurch wesentlich schwieriger wurde das Motorrad auszubalancieren. Wir haben uns daher dazu entschieden uns an der Bauweise aus dem [YouTube-Video](https://www.youtube.com/watch?v=IiCZoNBiXc0) zu orientieren. 

### Programmierung

Auch bei der Programmierung haben wir uns an dem [Programmier-Tutorial](https://www.youtube.com/watch?v=TupLmKkHMBU&t=0s) von der [Creator Academy Australia](https://www.youtube.com/watch?v=MCVW2Uqanlw) orientiert. Dabei sind wir auf verschiedene Probleme gestoßen. Im ersten Schritt haben wir den Code übernommen und geschaut, ob das Motorrad direkt in der Lage ist sich selbst auszubalancieren. Das war nicht der Fall. Das Motorrad ist in fast allen Testläufen nach wenigen Zentimetern umgekippt. Es gab einzelne Testläufe in denen das Motorrad in der Lage war wenige Meter zu fahren, was jedoch lediglich daran lag, dass das Motorrad in jenen Testläufen sehr lange aufrecht blieb und daher keine Lenkbewegungen notwendig waren. Es wurde recht deutlich, dass die Lenkbewgungen zu stark und zu ruckartig ausgeführt wurden. Daher haben wir versucht die Parameter (Kh, Kd, etc.) systematisch zu variieren und geschaut, bei welchen Veränderung die Stabilität des Motorrads erhöht wurde. Wir versuchten dabei die Parameter so anzupassen, dass die Lenkbewegungen sanfter durchgeführt werden. Wir konnten beobachten, dass die zurückgelegte Strecke größer wurde, wenn wir den Parameter "Kp", welcher den Fehler gewichtet, kleiner gemacht haben. Nach einigen Versuchen stellten wir fest, dass eine Halbierung des "Kp"-Wertes von 2 auf 1 unser Problem für die beste Stabilität sorgte. Die anderen Parameter beließen wir bei den Werten aus dem [Video](https://www.youtube.com/watch?v=TupLmKkHMBU&t=0s), wir stellten jedoch fest, dass das Motorrad auch ohne die Variable "Integral" in der Lage war zu fahren. 

Im Laufe des Tests stellten wir außerdem fest, dass die Variablen nach Beendigung des Programms nicht zurückgesetzt wurden, was zu Fehlern in der Berechnung der Lenkbewegungen führte. Wir lösten das Problem, wie bereits in der [Code-Erklärung](#Initialisierung-von-Variablen-und-Parametern) beschrieben, in dem wir  


Dabei haben wir jedoch sehr schnell festgestellt, dass die in dem Video gewählten Parameter für unser Modell nicht funktionieren. Daher haben wir begonnen systematisch die verschiedenen Parameter zu variieren und die Veränderungen in der zurückgelegten Distanz zu messen. Dabei machten wir kaum messbare Fortschritte. Auffällig war, dass das Motorrad auch bei kleinen Kippwinkeln sehr stark gegengelenkt hat und dadurch noch schneller umgekippt ist. Wir haben daher den Parameter (Kp), welcher den Fehler-Wert (Error) gewichtet von 2 auf 1 halbiert. Danach war das Motorrad in der Lage sich selbst auszubalancieren. Die anderen Parameter spielen dabei zum Teil eine untergeordnete Rolle. 

### Controller-Steuerung

Nachdem das Motorrad in der Lage war, sich selbst auszubalancieren, haben wir versucht eine Controller-Steuerung zu implementieren. Dabei sind wir leider auf verschiedene Probleme gestoßen, welche wir aus zeitlichen Gründen nicht mehr lösen konnten. Am entscheidensten war der Unterschied vom Download- zum Streaming-Modus. Während die Balancierung im Download-Modus, mit den oben gewählten Werten, problemlos funktioniert, ist das Motorrad im Streaming-Modus bei gleichem Code nicht mehr in der Lage zu fahren.  

### Unterschiede Spike- und Mindstorms-App

Troubleshooting nicht Connecten des Hubs in der Mindstorm App: Es ist anzumerken, dass es beim Bluetooth-Verbinden des aktualsierten Hubs (grün leuchtender Ring) Schwierigkeiten in der Mindstorms App gab. Daher mussten wir den Hub Downgraden -> Siehe link https://spikelegacy.legoeducation.com/hubdowngrade/#step-1 , um ihn dann in der Mindstorms App zu verbinden und dort erneut zu aktualisieren. Danach funktionierte des Bluetooth-Verbinden in der Spike und Mindstorm App problemlos.

[Aufbauanleitung](https://www.youtube.com/watch?v=IiCZoNBiXc0) von [Creator Academy Australia](https://www.youtube.com/watch?v=MCVW2Uqanlw).
