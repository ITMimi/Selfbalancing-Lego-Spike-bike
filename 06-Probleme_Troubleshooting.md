# Entwicklung / Probleme / Troubleshooting

Unser Ziel war es, ein selbstausbalancierendes Motorrad mithilfe des Lego-Spike-Sets zu bauen und zu entwickeln. Während der ersten Recherche sind wir auf den YouTube Kanal  

## Bauweise 

Wir haben damit begonnen uns über die Bauweise für das Motorrad Gedanken zu machen. Dabei war uns schnell klar, dass eine möglichst kompakte Bauweise entscheidend ist, um in der Lage zu sein das Motorrad später auszubalancieren. Unser erster Prototyp war wesentlich zu lang, was es kaum möglich machte, diesen auszubalancieren.  




## Bauweise

Zu Beginn haben wir eine weniger kompakte Bauweise für das Motorrad gewählt und damit die ersten Tests gemacht. Dabei ist uns schnell aufgefallen, dass die Kompaktheit einer der wichtigsten Faktoren ist, um das Motorrad ausbalancieren zu können. Daher haben wir uns aus zeitlichen Gründen dazu entschieden, uns an der Bauweise aus dem [YouTube-Video](https://www.youtube.com/watch?v=IiCZoNBiXc0) zu orientieren.  

## Programmierung

Auch bei der Programmierung haben wir uns an dem [Programmier-Tutorial](https://www.youtube.com/watch?v=TupLmKkHMBU&t=0s) von der [Creator Academy Australia](https://www.youtube.com/watch?v=MCVW2Uqanlw) orientiert. Dabei sind wir auf verschiedene Probleme gestoßen. Im ersten Schritt haben wir den Code übernommen und geschaut, ob das Motorrad direkt in der Lage ist sich selbst auszubalancieren. Das war nicht der Fall. Das Motorrad ist in fast allen Testläufen nach wenigen Zentimetern umgekippt. Es gab einzelne Testläufe in denen das Motorrad in der Lage war wenige Meter zu fahren, was jedoch lediglich daran lag, dass das Motorrad in jenen Testläufen sehr lange aufrecht blieb und daher keine Lenkbewegungen notwendig waren. Es wurde recht deutlich, dass die Lenkbewgungen zu stark und zu ruckartig ausgeführt wurden. Daher haben wir versucht die Parameter (Kh, Kd, etc.) systematisch zu variieren und geschaut, bei welchen Veränderung die Stabilität des Motorrads erhöht wurde. Wir versuchten dabei die Parameter so anzupassen, dass die Lenkbewegungen sanfter durchgeführt werden. Wir konnten beobachten, dass die zurückgelegte Strecke größer wurde, wenn wir den Parameter "Kp", welcher den Fehler gewichtet, kleiner gemacht haben. Nach einigen Versuchen stellten wir fest, dass eine Halbierung des "Kp"-Wertes von 2 auf 1 unser Problem löste und für die beste Stabilität sorgte. Die anderen Parameter beließen wir bei den Werten aus dem [Video](https://www.youtube.com/watch?v=TupLmKkHMBU&t=0s), wir stellten jedoch fest, dass das Motorrad auch ohne die Variable "Integral" in der Lage war zu fahren. 

Im Laufe des Tests stellten wir außerdem fest, dass die Variablen nach Beendigung des Programms nicht zurückgesetzt wurden, was zu Fehlern in der Berechnung der Lenkbewegungen führte. Wir lösten das Problem, wie bereits in der [Code-Erklärung](#Initialisierung-von-Variablen-und-Parametern) beschrieben, in dem alle Variablen im Code manuell zurückgesetzt werden.   

## Controller-Steuerung

Nachdem das Motorrad in der Lage war, sich selbst auszubalancieren, haben wir versucht eine Controller-Steuerung zu implementieren. Dabei sind wir leider auf verschiedene Probleme gestoßen, welche wir aus zeitlichen Gründen nicht mehr lösen konnten. Am entscheidensten war der Unterschied vom Download- zum Streaming-Modus. Der Streaming-Modus ist notwendig, um die Controller-Inputs registrieren und verarbeiten zu können. Während die Balancierung im Download-Modus, problemlos funktioniert, ist das Motorrad im Streaming-Modus bei gleichem Code nicht mehr in der Lage zu stabil fahren.  

## Connection zwischen Hub und Computer

Troubleshooting nicht Connecten des Hubs in der Mindstorm App: Es ist anzumerken, dass es beim Bluetooth-Verbinden des aktualsierten Hubs (grün leuchtender Ring) Schwierigkeiten in der Mindstorms App gab. Daher mussten wir den Hub Downgraden -> Siehe link https://spikelegacy.legoeducation.com/hubdowngrade/#step-1 , um ihn dann in der Mindstorms App zu verbinden und dort erneut zu aktualisieren. Danach funktionierte des Bluetooth-Verbinden in der Spike und Mindstorm App problemlos.
