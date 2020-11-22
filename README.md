<html>
<head>
<link rel="stylesheet" href="../style.css" type="text/css">
</head>
<body>
<h1>Transputer</h1>
Links:<br>
http://www.transputer.net/<br>
https://sites.google.com/site/transputeremulator/<br>
http://www.wehavemorefun.de/fritzbox/ISDN-Controller_B1_PCI<br>
http://jonathanschilling.de/content/elektrotechnik/computerbasteln/transputer/avm_b1<br>
http://www.classiccmp.org/transputer/software/languages/occam/compilers/inmos/commercial/<br>
http://www.geekdot.com/avm-b1.html<br>http://www.classiccmp.org/transputer/<br>
<br>
Viele Informationen hier sind durch die Arbeiten von <b>Axel Muhr</b> &amp; <b>Jonathan Schilling</b> erst ermöglicht worden! 
Siehe auch ihre Seiten unter Links.<br>
<br>
Transputer waren spezielle Chips/CPU's der Firma INMOS zur hoch parallelen Datenverarbeitung.<br>
Transputer Chips konnten über schnelle Link-Verbindungen zu Clustern aufgebaut werden.<br>
Als Hochsprache, die parallel Prozesse unterstützt wurde damals Occam entwickelt.<br>
Die Chips und Rechnerboards kamen ab 1983 auf dem Markt. Heute sind solche Boards nur noch sehr schwer zu bekommen und sehr teuer – mit Ausnahme.. <br>
<br>
Aber auf einer alten ISDN Karte B1 von AVM ist ein T400 Transputer Chip drauf und die Karte ist sogar registerkompatibel zur originalen INMOS B004 Karte!<br>
<br>
Der AVM B1 ist ein aktiver ISDN-Controller und bis Version 3.0 für den ISA-Bus gebaut. <br>
Bis Version 3.0 wird ein Transputer vom Typ T400 verwendet. V1+V2 sind geeignet.<br>
<br>
Bild AVB-B1 V2:<br>
(Pin-Anschlussreihe links nach rechts: 1-2-3-4-5-6-7-8-9-10)<br>
<img src="./AVM-B1V2.jpg"><br>
<br>Auf der linken Seite der Karte findet sich ein kleines Transputer-System mit T400 Transputer Chip (rechts oben rot markiert) und 1MB RAM sowie einem 
TRAM-ähnlichen Erweiterungsinterface. Rechts unten auf der Karte sitzt der C011, der auf den 4 jumperbaren Adressen (Mitte unten rot markiert) vom ISA-Bus 
aus angesprochen werden kann. Die Standardadresse sollte 0x150 sein! Der C011 ist auf der B1 fest auf Link 0 des T400 verdrahtet. Die Links sind von AVM 
auf der Platine auf 10MBit/s verdrahtet.<br>
<br>
Also alten DOS Rechner mit ISA Slots aufsetzen, Karte rein und schon hat man seinen eigenen, kleinen Transputer zuhause.<br>
<br>
Auf: http://www.wizzy.com/wizzy/ispy.html<br>
<br>
Gibt es die Tools ispy und mtest. Mit eingesetzter B1 Karte und Adressjumper auf 0x150 gesetzt, sollte eine Aufruf von ispy | mtest in der DOS Kommandozeile 
etwa folgende Rückmeldung erzeugen:<br>
<br>&gt; ispy | mtest Using 150 ispy 3.21 | mtest 3.21 <br>
# Part rate Link# [ Link0 Link1 Link2 Link3 ] RAM,cycle <br>0 T400b-20 43k 0 [ HOST ... ... ... ] 2K,1 1022K,6.<br>
<br>
So einfach hat man ein funktionierendes Transputersystem! Das Mandelbrot Programm kann so direkt gestartet werden und alles passt auf eine FreeDOS Bootdiskette 1,44MB.<br>
<br>
<a href="./Transp.zip">Transp.zip</a><br>
<br>
Übersetzte (Occam) Programme werden mit iserver.exe ausgeführt. Eine Batchdatei iserv.bat setzt dazu notwendige Umgebungsvariablen!
<br>
set IBOARDSIZE=#100000<br>
set TRANSPUTER=#150<br>
iserver.exe /SB %1 %2 %3 <br> 
<br>  
Man kann sogar 2 AVM B1 Karten in einem PC als kleines Transputer-Cluster betreiben. Eine Karte wird auf 0x150 gejumpert, die andere z.B. auf 0x160 
(damit wird sie ersteinmal nicht erkannt von der PC Software). Beide Karten werden nun über 3 kurze Verbindungen miteinander verbunden:<br>
(Dabei wird vorher der Reset-Pin auf Pin 2 der 10-poligen Leiste verdrahtet, wie auf J.Schillings Seite beschrieben)<br>
<br>Link1in(1) &lt;- Link1out(2) (Pin 8)<br>Link1out(1) -&gt; Link1in(2) (Pin 9)<br>Reset(1) &lt;-&gt; 
Reset(2)&nbsp;&nbsp;&nbsp;&nbsp; (Pin 2)<br>
<br>
Bild des Aufbaus und ispy Anzeige:<br><img src="./TP-Cluster1.jpg"><br>
<br>
Bild der Verbindungen:<br><img src="./TP-Cluster2.jpg"><br>
<br>
</body>
</html>
