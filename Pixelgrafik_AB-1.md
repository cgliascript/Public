# 1. Pixelgrafik



## Info-Blatt

In dieser Lektion werden wir uns mit den Grundlagen der Binärdarstellung von Bildern als Rastergrafiken beschäftigen, Merkmale von Rastergrafiken sowie einfache Dateiformate für Rastergrafiken kennenlernen.

> Für die Aufgaben später wirst du einige **Dateien** benötigen, die du unter folgendem [Link](https://github.com/cgliascript/Public) unter **"Pixelgrafik.rar"** finden kannst.

Wenn Du eine Bilddatei in einem Format wie JPG oder PNG in einem Bildanzeigeprogramm öffnest und stark vergrößerst, erkennst Du, dass das Bild aus einzelnen quadratischen Bildpunkten zusammengesetzt ist, die in einem Raster angeordnet sind. Aus diesem Grund wird dieses Bildformat als Rastergrafik bezeichnet.

![images](https://i.imgur.com/n1FDjYR.png)

Eine Rastergrafik beschreibt also Bilddaten in digitaler Form, indem das Bild in ein Raster von Bildpunkten, die sogenannten **Pixel** (kurz für engl. pixel elements), aufgeteilt wird und jedem Pixel ein diskreter Farbwert zugeordnet wird. Die wichtigsten Attribute einer Rastergrafik sind die **Bildgröße**, also Breite und Höhe (in Pixeln), sowie die **Farbtiefe**, also die Anzahl an Bits, die benötigt werden, um den Wert eines Pixels darzustellen. Wird beispielsweise nur 1 Bit pro Pixel verwendet, lassen sich nur 2 verschiedene Farbwerte pro Pixel unterscheiden (z. B. schwarz und weiß), während sich mit 8 Bit (also 1 Byte) bereits 2^8^ = 256 verschiedene Farbwerte darstellen lassen.

----

![images](https://i.imgur.com/1vHXjex.png)

----

<h3>Codierung eines Schwarz-Weiß-Bildes</h3>

Die Pixelwerte werden im Speicher üblicherweise zeilenweise von oben links nach unten rechts als Bitfolge repräsentiert. Ein Schwarz-Weiss-Bild kann für einen Computer („welcher nur 0 und 1 versteht“) relativ einfach codiert werden. Für jedes ausgefüllte Kästchen wird eine 1 geschrieben und für jedes leere Kästchen eine 0. Ein solches Bild hätte dann eine Farbtiefe von 1 Bit (2^1^ = 2 Farben). 

>**Beispiel:** Ein Bild der Größe 8 × 8 Pixel, die jeweils nur schwarz oder weiß sind, lässt sich als Bitfolge der Länge 64 Bit darstellen. Jedes Bit stellt ein Pixel dar (hier: 0 = weiß, 1 = schwarz).
>
>![images](https://i.imgur.com/eaJ14OC.png)

---

<br>

<h3>Graustufen-Bilder</h3>

In **Graustufenbildern** kann ein Pixel dagegen verschiedene Graustufen als Wert haben. Wird jedes Pixel durch 1 Byte (= 8 Bit) repräsentiert, bedeutet das etwa, dass 2^8^ = 256 verschiedene Graustufen im Bild vorkommen können. Der Wert 0 repräsentiert dabei schwarz, 255 weiß und die Werte 1 bis 254 in linearer Abstufung die dazwischen liegenden Grautöne.

<img src="https://i.imgur.com/LkchMUV.png" height="75px" width="200px">

---

<br>
<h3>Farb-Bilder</h3>

In **Farbbildern** wird pro Pixel üblicherweise ein Rot-, Grün- und Blauwert gespeichert (**R<!-- style = "color: red;" -->G<!-- style = "color: green;" -->B<!-- style = "color: blue;" -->-Werte**). Mit diesen drei Werten lassen sich alle Farben des **RGB-Farbraums** darstellen, in dem durch das additive Mischen der drei Grundfarben Rot, Grün und Blau jeder beliebige Farbeindruck nachgebildet wird. Gelb ergibt sich beispielsweise durch 100 % Rot<!-- style = "color: red;" --> + 100 % Grün<!-- style = "color: green;" --> + 0 % Blau<!-- style = "color: blue;" -->, während 50 % Rot<!-- style = "color: red;" --> + 75 % Grün<!-- style = "color: green;" --> + 100 % Blau<!-- style = "color: blue;" --> ein Himmelblau ergibt.
Alternativ kann auch ein “Farbpalette” verwenden werden zur Repräsentation von Bildern mit mehreren Farben. 

<img src="https://i.imgur.com/TcrQz5s.png" height="75px" width="200px"> <img src="https://i.imgur.com/jLmQNaf.png" height="200px" width="324px" align="right"> 

Wird für den Rot-, Grün- und Blauwert je 1 Byte verwendet, ergibt sich eine Farbtiefe von 3 Byte bzw. 24 Bit (3 Byte = 8 Bit --> 3 x 8 = 24), womit insgesamt (2^8^)^3^ = 2^24^ ≈ 16 Mio. verschiedene Farben pro Pixel darstellbar sind. Diese Werte liegen im Speicher in der Regel direkt aufeinanderfolgend in der Reihenfolge RGB (seltener auch in anderen Reihenfolgen wie BGR) und können als Hexadezimalcode mit sechs Ziffern (für 3 Byte) dargestellt werden:

<img src="https://i.imgur.com/rjtVZf8.png" height="200px" width="400px">

<br>
<br>

Jedes Pixel in einem RGB-Farbbild enthält also im Grunde drei Helligkeitswerte, nämlich jeweils einen 256-Bit-Wert für Rot, Grün und Blau. Die eigentliche Farbe des Pixels entsteht durch die Kombination dieser drei Werte. Ein Farbbild lässt sich also auch durch drei Bilder repräsentieren, bei denen jedes Pixel nur je einen 256-Bit-Wert hat, nämlich entweder den Rot-Wert, Grün-Wert oder Blau-Wert des Farbbildes. Die so repräsentierten Bilder werden als **Farbkanäle** bezeichnet:

<img src="https://i.imgur.com/agGyt50.png" height="200px" width="800px">

<br>
<br>

Ein RGB-Bild wird dementsprechend auch als Mehrkanal-Bild bezeichnet, das sich aus dem Rot-, Grün- und Blaukanal zusammensetzt, während ein Graustufenbild (bzw. auch ein Binärbild) ein Einkanal-Bild ist.

In den getrennten Darstellungen der Kanäle lässt sich gut erkennen, welche Farbe aus welchen Rot-, Grün- und Blau-Anteilen zusammengesetzt ist: Die gelben Bildbereiche auf dem Leuchtturm enthalten hohe Anteile Rot und Grün, aber kaum Blau, während die hellen himmelblauen Bereiche im Hintergrund hohe Grün-/Blau-Anteile und einen etwas geringeren Rot-Anteil enthalten. Diese Informationen sind unteranderem bei der Bildbearbeitung sehr wichtig.  

## Codierung von Pixelgrafiken

Damit ein Computer oder ein Handy Bilder darstellen kann, müssen diese *kodiert* werden.

> <h3>Aufgabe</h3>
> Klicke auf das erste Bild und betrachte schrittweise die folgenden Bilder, indem du auf das Pfeil rechts drückst. Beschreibe, was du erkennst.

![img](https://i.imgur.com/Qn4zSqX.jpeg)![img](https://i.imgur.com/J4tKQ2W.jpeg) ![img](https://i.imgur.com/Z3jP3qO.jpeg) ![img](https://i.imgur.com/EOlPkBv.jpeg) ![img](https://i.imgur.com/8d4A5uE.jpeg) ![img](https://i.imgur.com/PAjHwwq.jpeg)

<details>

<summary>**Lösung**</summary>

  Beim Vergrößern des Bildes werden immer mehr kleine Quadrate sichtbar. Das Bild setzt sich aus ganz vielen solcher Quadrate zusammen, man nennt sie **Pixel**. Diese Pixel benötigt der Computer, um Bilder zu codieren. 
  Unser Auge setzt diese winzig kleinen Quadrate zu einem vollständigen Bild zusammen. Je kleiner das Bild wird, desto besser kann unser Auge die kleinen Quadrate zu einem Bild zusammen setzen.

</details>

>In der Computergrafik bezeichnen wir die Größenänderung eines digitalen Bildes als **Skalierung**.


### Sklaierung

Eine verlustfreie Skalierung mit Pixelgrafiken ist nicht möglich. Jede Veränderung der Größe führt zu einer Verringerung der Qualität. Bei einer Vergrößerung fällt der Qualitätsverlust deutlich höher aus als bei einer Verkleinerung, da sich bei gleichbleibender Pixelzahl die Bildauflösung und absolute Pixelgröße vergrößert. Zwar bieten einige Bildbearbeitungsprogramme diverse Algorithmen zum Ausgleich an, wie etwa Pixelwiederholungen. Dennoch wird die Grafik bei Vergrößerungen unschärfer und bei einer Verkleinerung entfallen Details durch die Verringerung der Pixelanzahl.

![images](https://i.imgur.com/HzgAIrk.jpeg)

### Bilder mit Zahlen darstellen

Eine Möglichkeit, Bilder mit Pixeln darszustellen, bietet das **PBM-Format** ("Portable Bitmap"). Es besteht nur aus schwarzen und weißen Pixeln.
Mit dem Grafikeditor **CodeMyPic** *(siehe unten)* lassen sich Pixelgrafiken kodieren. Die Kodierung wird **Quelltext** genannt. 
Eine Änderung im Quelltext links wirkt sich unmittelbar auf die dargestellte Grafik rechts aus. 

> <h3>Aufgabe 1</h3>
> a) Lade die Datei **"Herz.pbm"** in den Editor. Erkunde die folgende Codierung mit der dazugehörigen Grafik, indem du den Code veränderst. Wofür stehen die Zahlen 0 und 1?
>
> b) Verändere den Code so, dass anstatt des Herzes ein Haus oder ein Smiley dargestellt wird.

??[CodeMyPic: Erster Test](https://codemypic.de)

> <h3>Aufgabe 2</h3>
> Lade die Datei **"Smiley.pbm"** in den Editor. Verändere den Smiley so, dass noch weitere Stimmungen (traurig, neutral, lachend,...) dargestellt werden können.

## Farbmodi

> In diesem Abschnitt lernen wir, wie verschiedene Bilder in unterschiedlichen Farbmodi dargestellt werden können.

### Schwarz-Weiß-Bilder

Das **PBM-Format** ("Portable Bitmap") wird benutzt, um zweifarbige Bilder darzustellen. Die Zahl **0** steht für die Farbe **weiß**, die Zahl **1** für die Farbe **schwarz**.

Um die Größe eines PBM-Dokuments zu verändern, kann man den **Kopf** (die ersten beiden Zeilen) verändern.

![img](https://i.imgur.com/drA6In6.png)

* Die erste Zeile **(P1)** steht für das **Format** PBM (denn es gibt auch noch andere Formate, die wir auf den nächsten Seiten noch kennenlernen werden)
* Die zweite Zeile gibt an, aus wie vielen **Spalten** (hier **5**) und wie vielen **Zeilen** (hier auch **5**) ein PBM Dokument bestehen soll.

> <h3>Aufgabe 1</h3>
> Lade die Datei **"Haus.pbm"** in den Editor. Erkunde den Kopf des PBM-Dokuments, indem du weitere Spalten und Zeilen hinzufügst, um ein größeres Haus zu zeichnen.
>
>Brauchst du dazu zum Beispiel 7 Spalten und 3 Zeilen, dann schreibe in die zweite Zeile "7 3" anstatt "5 5".

??[CodeMyPic: Erster Test](https://codemypic.de)

> <h3>Aufgabe 2</h3>
> Lade die Datei **"Name.pbm"** in den Editor. Hier hat Kevin das PBM-Format verwendet, um seinen Namen zu schreiben. Verändere den folgenden Code so, dass auch du deinen Namen, deinen Spitznamen, ein anderes schönes Wort oder ein tolles Bild zeichnen kannst.
>
> Dein Ergebnis kannst du unter einem passenden Dateinamen speichern.

### Graustufen-Bilder

Der Computer kann natürlich nicht nur scharz-weiße Bilder mit 0 und 1, sondern auch Bilder in verschiedenen Graustufen verarbeiten.

> <h3>Aufgabe 1</h3>
> Lade die Datei **"Ente.pbm"** in den Editor. Ersetze in dem Code alle **1**er durch **4**en: Was passiert mit dem Schnabel der Ente?
>
>Erkunde: Was bedeuten die Zahlen **0-5**?

??[CodeMyPic: Erster Test](https://codemypic.de)

> <h3>Aufgabe 2</h3>
> Lade die Datei **"Baum.pgm"** in den Editor. Finde durch Ausprobieren heraus, was die Zahl **15** aus der **dritten Zeile** bedeuten könnte (setze für diese z.B. 20, 50 oder 100 ein).

#### PGM-Format

Das **PGM-Format** ("Portable Graymap") wird benutzt, um Graustufen-Bilder darzustellen.

Der Kopf eines PGM-Dokuments beginnt mit **P2** (für das Format PGM), gefolgt von der **Spalten-** und **Zeilenanzahl** (hier 7 und 9):

![img](https://i.imgur.com/fbkYZTy.png)

Bei dem PGM Dokument wurde der Kopf um eine weitere Zeile erweitert: Der **Maximalwert** für die Helligkeit (hier die Zahl 15 aus der dritten Zeile): Die Zahl **15** wurde als **weiß** festgelegt. Die Zahl **0** stellt die Farbe **schwarz** dar. Die Zahlen **zwischen 0 und 15** stellen **Graustufen** dar.

> <h3>Aufgabe</h3>
> Erstelle ein PGM-Graustufen-Bild eines Hauses. Das Dach soll dunkler dargestellt sein als das Erdgeschoss. Die Fenster und Türen sollen am dunkelsten sein. 
>Speichere dein Ergebnis unter einem passenden Dateinamen ab.

??[CodeMyPic: Erster Test](https://codemypic.de)

### RGB-Bilder

Lade die Datei **"Buntes_Haus.ppm"** in den Editor. Hier siehst du ein Bild der Villa Kunterbunt und den dazugehörigen Quelltext. 

Jedes Kästen wird aus einer Zahlenkombination aus drei Ziffern zwischen 0 und 1 dargestellt (jeweils ein Leerzeichen dazwischen): Zum Beispiel das **Kästchen ganz links oben** wird codiert mit **1 1 1**. Das nächste Kästchen rechts trennen wir dieses mal mit *drei Leerzeichen* vom ersten Kästchen. 

??[CodeMyPic: Erster Test](https://codemypic.de)

> <h3>Aufgabe 1</h3>
> Verändere im Editor die Zahlenkombinationen für einzelne Kästchen und finde heraus, welche Kombinationen, welche Farbe darstellen. Ordne hierzu die folgenden Zahlenkombinationen den jeweiligen Farben zu:

??[DD](https://learningapps.org/watch?v=p5901p2u320)

> <h3>Aufgabe 2</h3>
> Verändere die Villa Kunterbunt so, dass sie aussieht, wie auf diesem Bild:
>![img](https://i.imgur.com/E3MPfjw.png)
> Speichere dein Ergebnis unter einem passenden Dateinamen ab.

#### PPM-Format

Das PPM-Format ("Portable Pixmap") wird benutzt, um bunte Bilder (RGB-Bilder - RGB = **R**ot **G**rün **B**lau) darzustellen.

Der Kopf eines PPM-Dokuments beginnt mit **P3** (für das Format PPM), gefolgt von der **Spalten-** und **Zeilenanzahl** (hier 2 und 3):

![img](https://i.imgur.com/NxPocyM.png)

Bei dem PPM Dokument wurde der Kopf um eine weitere Zeile erweitert: Der **Maximalwert** für die Helligkeit (hier die Zahl 1 aus der dritten Zeile).

Ein Pixel (Kästchen) wird bei dem PPM-Format mit einem "Dreierpäckchen" aus drei Ziffern dargestellt - die erste Ziffer entspricht dem **Rot**anteil, die zweite dem **Grün**anteil und die dritte dem **Blau**anteil, zum Beispiel:

* 1 0 0 = Rot            <img src="https://i.imgur.com/Fm5HL4e.png" height="200px" width="200px" align="right">
* 0 1 0 = Grün          
* 0 0 1 = Blau
* 0 0 0 = Schwarz
* 1 1 1 = Weiß
* 1 1 0 = Mischung aus Rot und Grün = Gelb
* 1 0 1 = Mischung aus Rot und Blau = Rosa (Magenta)
* 0 1 1 = Mischung aus Grün und Blau = Hellblau (Cyan)

> <h3>Aufgabe 1</h3>
> Lade die Datei **"Ente-RGB.ppm"** in den Editor. Verändere das Bild der Ente so, dass der Kopf gelb, der Schnabel rot und das Auge schwarz ist. Speichere dein Ergebnis unter einem passenden Dateinamen ab.
>
> <img src="https://i.imgur.com/WiCpQrS.png" height="200px" width="200px">

??[CodeMyPic: Erster Test](https://codemypic.de)

> <h3>Aufgabe 2</h3>
> Verändere den Maximalwert der Helligkeit (1 in der dritten Zeile) in die Zahl 2. Jetzt kann man noch mehr Farben darstellen, wie zum Beispiel orange. Findest du noch mehr Farben?
>
> *~~Tipp:~~ In jedem "Dreierpäckchen" können nun die Ziffern 0, 1 und 2 verwendet werden, teste zum Beispiel 2 0 2.*



## Ältere Aufgaben

### Aufgabe 1

Übertrage das untenstehende 12x12 Raster in dein Heft. 

Zeiche darin ein Smiley ein, indem du einzelne Quadrate des Rasters schwarz/farbig ausfüllst. 

![images](Bilder\12x12-Raster.png)

Überlege, wie der Smiley mithilfe eines Computers dargestellt werden kann und notiere deine Ideen in dein Heft!


### Aufgabe 2

Übertrage die nachfolgende Grafik, sowie den Smiley aus ~~Aufgabe 1~~ in die PBM-Kodierung (PortableBitmap). Verwende hierzu den Editor CodeMyPic. 

![images](Bilder\Haus_1.png)

Dokumentiere, wie du dabei vorgegangen bist. Eine geeignete Größe für das Raster ist 15×25.

---

??[CodeMyPic: Erster Test](https://codemypic.de)


### Aufgabe 3

Herr/Frau hat Dateien erstellt, leider sind ihm/ihr dabei ein paar Fehler unterlaufen.
Öffne die Dateien, um im Anschluss die Fehler zu finden und zu korrigieren.

(Dateinamen: Bild1.pbm, Bild2.pbm und Bild3.pbm)

---

??[CodeMyPic: Erster Test](https://codemypic.de)

### Aufgabe 4

Erstelle eine eigene Grafik mithilfe von CodeMyPic z.B. deinen Namen.

---

??[CodeMyPic: Erster Test](https://codemypic.de)

### Aufgabe 5

Betrachte die folgende Grafik. Notiere die/den Unterschied/e zu der vorherigen Grafik.

![images](Bilder\Haus_2.png)

### Aufgabe 6

Übertrage dein Smiley aus der Aufgabe 1 in die PGM-Kodierung, sodass dein Bild mehrere Graustufen enthält.

### Aufgabe 7

Bei den erstellten Dateien handelt es sich um sogenannte Pixelgrafiken. Beschreibe in eigenen Worten, was die Merkmale einer solchen Pixelgrafik sind.