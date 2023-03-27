<!--
author:   Yannic Bur

email:    ybur@uni-koblenz.de

version:  0.0.1

language: de

narrator: German Female

logo:     https://i.imgur.com/WO8Qf6c.jpg

comment:  Lia-Script Kurs zum Kennenlernen von Vektorgrafiken.

link:     https://cdn.jsdelivr.net/chartist.js/latest/chartist.min.css

script:   https://cdn.jsdelivr.net/chartist.js/latest/chartist.min.js

translation: Deutsch  translations/German.md

translation: Français translations/French.md
-->

# 2. Vektorgrafiken

In diesem Kurs werden Vektorgrafiken eingeführt. Es werden die Vorteile von Vektorgrafiken gegenüber Pixelgrafiken dargestellt. Weiter werden die Grundlagen zur Erstellung eines Bildes mit Vektorgrafiken eingeführt. Währenddessen haben die Lernenden die Möglichkeit, mit ihrem erlernten Wissen in einem Vektorprogramm selbst Grafiken zu erstellen.

## Pixelgrafiken _(Wiederholung)_

In unserem vorherigen Kurs haben wir gelernt, wie wir ein Bild Pixel für Pixel erstellen können. Hierbei können wir jedem Pixel einzelne Farbwerte zuweisen und unser Bild Pixel für Pixel erstellen.

In diesem Beispiel wurde ein Haus mit einer in schwarz-weiß als Pixelgrafik codiert.

![Pixelgrafik](https://i.imgur.com/KPKJYG5.png)

### Grenzen von Pixelgrafiken

> **Aufgabe 1** <br>
> Betrachtet die folgenden Bilder. Bennent was euch auffällt.

![Kreta_01](https://i.imgur.com/HU8k5YM.jpg)
![Kreta_04](https://i.imgur.com/STBvbiY.jpg)

![Blütenkirsche_01](https://i.imgur.com/mYfa1UC.jpg)
![Blütenkirsche_03](https://i.imgur.com/BoCl6q8.jpg)




{{1}}
********************************************************************************
> **Aufgabe 2:** <br>
> Kreuze die Felder an, welche mögliche Nachteile von Pixelgrafiken sind. <br>

[[X]] Können nicht auf jeder Größe dargestellt werden.
[[ ]] Haben eine eingeschränkte Farbauswahl.
[[x]] Verbrauchen viel Speicherplatz.
[[x]] Sind pixelig.

********************************************************************************

{{2}}
********************************************************************************

**Erklärung** <br>
Wenn wir Pixelgrafiken auf einem Bildschirm darstellen wollen, welcher größer oder kleiner als das Format der Pixelgrafik ist, kommt es zu Problemen. <br>
Ist die Pixelgrafik kleiner als unser Bildschirm, wird die Pixelgrafik zur Bildschirmgröße vergrößert, sodass eine genaue Zuordnung der Bildschirmpixel zu den Pixeln der Pixelgrafik nicht mehr möglich ist. Somit wird ein Pixel der Pixelgrafik auf mehreren Pixeln des Bildschirms dargestellt, wodurch die einzelnen Pixel der Pixelgrafik erkennbar werden. <br>
Wenn die Pixelgrafik hingegen größer ist als unser Bildschirm, werden mehrere Pixel der Grafik auf einen Pixel des Bildschirms abgebildet.

********************************************************************************

{{3}}
********************************************************************************
Im dem Beispiel dieses Hauses nimmt ein Pixel der Pixelgrafik vier nebeneinander liegende Pixel des Bildschirms ein, wodurch die Pixel der Pixelgrafik sichtbar werden.
Jedoch wären auf dieser Auflösung des Bildschirms eine bessere Auflösung möglich, wie danaebn dargestellt.

![Haus 1](https://i.imgur.com/Nrvla72.png)
![Haus 2](https://i.imgur.com/dzFkl8p.png)

Wir wollen uns im folgenden mit dem Problem der Skalierbarkeit, der darstellungen von Grafiken auf unterschiedlich großen Bildschirmen, beschäftigen.

********************************************************************************


## Vektorgrafiken
Wir werden nun mehrere kleine Experimente mit Grafiken durchführen.

> **Aufgabe 1:** <br>
> Zeichnet einen Stern als Pixelgrafik auf ein kariertes Blatt Papier. Verwendet hier für jedes Pixel ein Kästchen des Papiers. <br>
> Beschreibt euer Vorgehen.


{{1}}
********************************************************************************

> **Aufgabe 2:** <br>
> Überlegt euch wie ein Computer die Aufgabe 1 lösen würde. Ordnet dann die folgenden Arbeitsschritte, in eine für einen Computer sinnvollen Reihenfolge. _(Es gibt mehr Antworten als benötigte Lösungen)_

- [[1] (2) (3)]
- [( ) ( ) (x)] Ausmalen der eingeschloßenen Fläche.
- [( ) ( ) ( )] Erechnen der einzelnen Pixel durch eine vorgegebene Formel.
- [(x) ( ) ( )] Zeichnen des Umrisses des Sterns.
- [( ) (x) ( )] Bestimmen der Randpixel.


********************************************************************************

{{2}}
********************************************************************************
Euer Vorgehen zum Malen einer Pixelgrafik wird auch in der Vektorgrafik verwendet.
Zuerst wird eine Fläche durch einen Umriss, hier aus Geraden, erzeugt. Anschließend berechnet der Computer die Pixel des Umrisses und füllt die darin enthaltene Fläche aus. Dies nennt man **Rasterisierung**.

> __Vektorgrafiken__ sind Grafiken welche Punkten und Verbinidungslinien zwischen diesen Punkten bestehen. Um eine Vektorgrafik darzustellen muss aus dieser mit der __Rasterisierung__ eine Pixelgrafik in der Bildschirmgröße berechnet werden.

********************************************************************************

### Rasterisierung
Im folgenden Video haben wir ein Dreieck als Vektorgrafik vorliegen. Das Dreieck wird durch seine drei Eckpunkte und den Verbindungsgeraden zwischen den Eckpunkten dargestellt. <br>
Wir werden nun die Vektorgrafik des Dreiecks in eine Darstellung in Pixelgrafik umwandeln.

!?[Rasterisierung](https://youtu.be/8jycuXDPZGQ)

{{1}}
********************************************************************************

Da wir je nach Bildschirmgröße unsere Pixelgrafik aus unserer Vektorgrafik neu berechnen, passt die Größe der errechneten Pixelgrafik genau zur Größe unseres Bildschirms. Somit entsteht bei  Vektorgrafiken immer ein klares Bild welches nie verpixelt sein kann.

********************************************************************************

### SVG-Editor
Nun kennt ihr die Idee hinter Vektorgrafiken. <br>
Um Vektorgrafiken zu erstellen, benutzt man Vektorgrafikprogramme, wie den SVG-Editor. <br>
<br>
**Einführung in den SVG-Editor:** <br>

!?[SVG_01](https://youtu.be/XNr82b39vi0)

{{1}}
********************************************************************************

> **Arbeitsauftrag:** <br>
> a) Erstellt im SVG-Editor einen Stern, mit der im Video vorgestellten Funktionen. <br>
> b) Erstellt danach einen Mond, um dem Stern Gesellschaft zu leisten. <br>

<br>
[SVG-Editor](https://svgedit.netlify.app/editor/index.html "Vektorgrafikprogramm")
<br>
<br>

********************************************************************************

{{2}}
********************************************************************************

> **Aufgabe 1:**
> Auf welches Problem seit ihr bei dem Erstellen des Mondes gekommen? <br>
> Notiert eure Überlegungen.

********************************************************************************

{{3}}
********************************************************************************
> **Aufgabe 2:** <br>
> Welche der folgenden Motive könnt ihr mit den euch bekannten Funktionen im SVG-Editor erstellen? Und welche nicht?

- [[erstellbar] (nicht erstellbar)]
- [( ) (x)] eine Sonne
- [(x) ( )] ein Haus
- [( ) (x)] ein Baum
- [(x) ( )] eine Parkbank
- [( ) (x)] einen Hund
- [( ) (x)] eine Blume

********************************************************************************

{{4}}
********************************************************************************

> **Aufgabe 3:** <br>
> Untersucht die Motive aus Aufgabe 2 auf Gemeinsamkeiten und notiert diese. Vergleicht anschließend die Gemeinsamkeiten mit euren Überlegungen aus Aufgabe 1. <br>

********************************************************************************

{{5}}
********************************************************************************

__Erklärung:__ <br>
Alle bisher nicht erstellbaren Motive, wie der Mond, die Sonne oder eine Blume, beinhalten gekrümmte Linien. Diese können wir noch nicht im SVG-Editor darstellen. Um dies zu tun, benötigen wir eine neue Funktion, die Bezier Kurven.

********************************************************************************

## Bezier Kurven
Wir können bisher nur gerade Linien im SVG-Editor zeichnen. <br>
Aber was wäre wenn wir gekrümmte Linien zeichnen könnten?

{{1}}
********************************************************************************

Gekrümmte Linien können wir mit Kurven beschreiben. Hier müssen wir einen Weg finden, das wir diese Kurven aus so wenig Informationen wie möglich erstellen können. <br>
<br>

********************************************************************************

{{2}}
********************************************************************************

Die Kurven die ihr aus dem Matheunterricht kennt, sind zu unflexibel für das freie Erstellen von Vektorgrafiken. <br>
Aus diesem Grund betrachten wir die **Bezier Kurven**. <br>
<br>

********************************************************************************

{{3}}
********************************************************************************
Die Bezier Kurven werden aus aus nur einem Startpunkt _(Start)_ einem Endpunkt _(Ende)_ une einem oder zwei Hilfspunkten berechnet _(H1 und H2)_. <br>
<br>

> **Aufgabe:** <br>
> Verschiebt die Punkte _Start_, _Ende_, _H1_ und _H2_ in den einzelnen Grafiken. Beobachtet das Verhalten der Bezier Kurven und notiert, wie sich die Kurve dadurch verändert. <br>

<br>
__Bezier Kurve mit einem Hilfspunkt (Kurve 2. Grades)__ <br>

<iframe scrolling="no" title="Bezier Kurve vom Grad 2" src="https://www.geogebra.org/material/iframe/id/dwrardyn/width/700/height/500/border/888888/sfsb/true/smb/false/stb/false/stbh/false/ai/false/asb/false/sri/false/rc/false/ld/false/sdz/false/ctl/false" width="700px" height="500px" style="border:0px;"> </iframe>

<br>
__Bezier Kurve mit zwei Hilfspunkten (Kurve 3. Grades)__ <br>
<iframe scrolling="no" title="Bezier Kurve vom Grad 3" src="https://www.geogebra.org/material/iframe/id/p5xvgpdh/width/700/height/500/border/888888/sfsb/true/smb/false/stb/false/stbh/false/ai/false/asb/false/sri/false/rc/false/ld/false/sdz/false/ctl/false" width="700px" height="500px" style="border:0px;"> </iframe>

********************************************************************************

### Kurven 2. Grades
Mit den Bezier Kurven 2. Grades können wir einfache Kurven erstellen. <br>
Um die Kurve zu erstellen, benötigen wir die drei Punkte den Startpunkt _Start_, den Endpunkt _Ende_ und den Hilfspunkt _H1_. <br>
<br>
__Konstruktion einer Bezier Kurve:__ <br>
!?[Bezier Grad 2](https://youtu.be/R0xiLdZUepI)
<br>
Um einen **Punkt der Kurve P** für unser Verhältnis _n : 1-n_ zu bestimmen, müssen die Verbindungsstrecke von unserem Startpunkt _Start_ zu unserem Hilfspunkt _H1_ und die Verbindungstrecke von unserem Hilfspunkt _H1_ zum Endpunkt _Ende_, im gewählten Verhältnis geteilt werden, was uns die Punkte **A** und **B** liefert. In unserem Beispiel ist das Verhältnis bei jeder Strecke durch die grünen und lila Streckenteile gekennzeichnet und beträgt _n_ = 0,4 (grün) zu _1-n_ = 0,6 (lila). <br>
<br>
Die Verbindungsstrecke zwischen _A_ und _B_ wird nun auch im gleichen Verhältnis geteilt, wobei uns dies den **Punkt _P_** zu unserem Verhältnis liefert, welcher auf der Bezier Kurve liegt. <br>
<br>

> **Aufgabe 1:** <br>
> Veranschaulicht euch das Prinzip der Ertstellung von Bezier Kurven anhand der Grafik, wobei ihr hier den Faktor _n_ eures Verhältnisses beliebig wählen könnt.
<br>

<iframe scrolling="no" title="Bezier Kurve vom Grad 2" src="https://www.geogebra.org/material/iframe/id/whtnwra8/width/700/height/500/border/888888/sfsb/true/smb/false/stb/false/stbh/false/ai/false/asb/false/sri/false/rc/false/ld/false/sdz/false/ctl/false" width="700px" height="500px" style="border:0px;"> </iframe>
<br>
<br>

> **Aufgabe 2:** <br>
> a) Zeichtnet auf einem Blatt Papier die drei Punkte _Start_, _Ende_ und _H1_. Konstruiert die Punkte der Bezier Kurve, nach dem oben vorgestellten Vorgehen für die Verhältnisse <br>
> 0,25 : 0,75 _(ein Viertel zu drei Vierteln )_, <br>
> 0,5 : 0,5 _(ein Halb zu ein Halb)_ und <br>
> 0,75 : 0.25 _(drei Viertel zu ein Viertel)_ <br>
> b) Zeichnet anschließend eine Bezier Kurve vom Startpunkt _Start_ zu dem Endpunkt _Ende_, wobei die Kurve durch alle von euch konstruierten Punkte verläuft. <br>
> c) Überprüft nun die von euch konstruierte Bezier Kurve mit der interaktiven Grafik, wobei ihr die Punkte _Start_, _H1_ und _Ende_ entsprechend euerer Grafik anpassen müsst. Den Wert _n_ wählt ihr dabei nach dem ersten Wert des Verhältnisses.

### Kurven 3. Grades
Bezier Kurven vom Grad 3, können durch ihre zwei Hilfspunkte einfacher angepasst werden. Auch lassen sich mit ihnen einfach nahtlose Übergänge zweischen mehreren aneinander gereihten Bezier Kurven erstellen. Aus diesem Grund werden Bezier Kurven vom Grad 3 am häufigsten in Vektorgrafiken verwendet. <br>
<br>
Ihre Konstruktion verläuft ähnlich zu der Konstruktion von Bezier Kurven mit nur einem Hilfspunkt. <br>

!?[Bezier Grad 3](https://youtu.be/97xQ2FwX4w0)

<br>
Um einen **Punkt der Kurve P** für unseren Verhältnis _n : 1-n_ zu bestimmen, muss die Verbindungsstrecke von unserem Startpunkt _Start_ zu unserem Hilfspunkt _H1_, die Verbindungsstrecke zwischen unseren Hilfspunkten _H1_ und _H2_ und die Verbindungstrecke von unserem Hilfspunkt _H2_ zum Endpunkt _Ende_, im gewählten Verhältnis geteilt werden, was uns die Punkte **A** **B** und **C** liefert. In unserem Beispiel ist das Verhältnis bei jeder Strecke durch die grünen und lila Streckenteile gekennzeichnet und beträgt _n_ = 0,4 (grün) zu _1-n_ = 0,6 (lila). <br>
<br>
Die Verbindungsstrecken zwischen _A_ und _B_ und _B_ und _C_ werden nun auch im gleichen Verhältnis geteilt, wobei hier die Punkte _D_ und _E_ konstruiert werden. <br>
<br>
Der Punkt auf unserer Bezier Kurve __*P*__ zu unserem Verhältnis _n : 1-n_ erhalten wir, indem wir die Stecke zwischen _D_ und _E_ wieder in unserm Verhältnis teilen. <br>
<br>

Ihr habt hier die Möglichkeit das Verfahren an der Grafik für ein beliebiges Verhältnis nachzuvollzienen, wobei n der erste Wert eures Verhältnisses ist. <br>

<iframe scrolling="no" title="Bezier Kurve vom Grad 3" src="https://www.geogebra.org/material/iframe/id/gsydwd4p/width/700/height/500/border/888888/sfsb/true/smb/false/stb/false/stbh/false/ai/false/asb/false/sri/false/rc/false/ld/false/sdz/false/ctl/false" width="700px" height="500px" style="border:0px;"> </iframe>

### Bezier Kurven im SVG-Editor
Nun wollen wir Bezier Kurven im SVG-Editor kennen lerenen. <br>
!?[SVG_02](https://youtu.be/7qtBU_6AEXo)

> **Arbeitsauftrag:** <br>
> a) Erstelle im SVG-Editor ein Herz mit Hilfe von Bezier Kurven. <br>
> b) Erstelle im SVG-Editor einen Baum mit Hilfe von Bezier Kurven. <br>
> c) Erstelle im SVG-Editor eine Wolke mit Hilfe von Bezier Kurven. <br>

## Abschlussprojekt

Nun könnt ihr euer Wissen über Vektorgrafiken nun anwenden.<br>
Ihr findet hier weiter Funktionalitäten des SVG-Editors. <br>
!?[SVG_02](https://youtu.be/Jw94ORBKLFs)

> **Arbeitsauftrag:** <br>
> Erstellt ein Wappen mit einem Motiv eurer Wahl im SVG-Editor. <br>
