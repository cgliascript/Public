<!--
author:   Florian Schroers

email:    fschroers@uni-koblenz.de

version:  1.0.2

language: de

narrator: Deutsch Male

logo:     https://i.stack.imgur.com/GEsdl.jpg

comment:  LiaScript-Kurs zum Kennenlernen von Filtern in der Bildbearbeitung

link:     https://cdn.jsdelivr.net/chartist.js/latest/chartist.min.css

import:   https://raw.githubusercontent.com/liaTemplates/WebDev/master/README.md
          https://raw.githubusercontent.com/liaScript/rextester_template/master/README.md
          https://github.com/LiaTemplates/KekuleJS
          https://github.com/LiaTemplates/VTK
          https://github.com/LiaTemplates/Algebrite
          https://github.com/LiaTemplates/ProcessingJS
          https://github.com/LiaTemplates/mec2/blob/main/README.md

script:   https://cdn.jsdelivr.net/chartist.js/latest/chartist.min.js
          https://cdn.rawgit.com/davidedc/Algebrite/master/dist/algebrite.bundle-for-browser.js


translation: Deutsch  translations/German.md

translation: Français translations/French.md


-->

# 3. Filter

![image](https://i.stack.imgur.com/GEsdl.jpg)

Guten Tag. Schön, dass du diesen Kurs besuchst. Ein paar Anmerkungen bevor wir loslegen. Im Unteren Bildbereich kannst du dich über die Pfeiltasten vor und zurück im Kurs bewegen. Du kannst auch dafür das Menü auf der linken Seite verwenden.

Immer wenn das der Button mit dem Zeichen </> erscheint, handelt es sich im Programmcode der ausgeführt werden kann. Klicke dann immer auf das Symbol und es passiert etwas.

>Wichtige Anmerkungen und Tipps werden so angezeigt.

Dann mal los und viel Spaß!

## Filtermasken & Rasterisierung

Was ist eine Filtermaske? Schau dir dazu dieses Video an.

!?[video](https://youtu.be/kEbven3np5E)

### Wiederholung: Rasterisierung

> * geometrische Formen werden in ein Raster gelegt
> * Pixel werden ausgefüllt, wenn die Grafik über 50% der Pixelfläche bedeckt

![image](https://i.imgur.com/RhZj7si.jpeg)

Das rote Dreieck und der rote Kreis sind eine ...

  [(X)] ... Vektorgrafik.
  [( )] ... Pixelgrafik.

Die gelben Kästchen sind eine ... 

  [( )] ... Vektorgrafik.
  [(X)] ... Pixelgrafik.

Mittels der Rasterisierung eines Bildes werden aus ...

  [(X)] ... Vektoren Pixel erzeugt.
  [( )] ... Pixel Vektoren erzeugt.

## Medianfilter

Schau dir das Video an, um zu verstehen, wie der Medianfilter funktioniert.

!?[video](https://youtu.be/AD_pThmbkl0)

### Quiz Salz-und-Pfeffer-Rauschen

{{1}} **Recherchiere im Internet nach Salz-und-Pfeffer-Rauschen und beantworte anschließend die Fragen.**

{{2}} **Baentworte nun die Fragen.**

Was ist Salz-und-Pfeffer-Rauschen?

  [( )] Wenn man kein Signal am einem analogen TV-Eingang hat.
  [(X)] Ein zufälliges Auftreten von weißen bzw. schwarzen Pixeln auf einem Bild.
  [( )] Ein Bild, das nur aus schwarzen und weißen Pixeln besteht.
  [( )] Ein gleichmäßiges und kalkuliertes Auftreten von weißen bzw. schwarzen Pixeln auf einem Bild.


Welche Ursachen kann das Salz-und-Pfeffer-Rauschen haben?

  [[X]] Durch Staubpartikel auf Scanner bzw. Linse
  [[ ]] Fotografieren beim Kochen
  [[X]] Fehlerhafte Sensoren bei Digitalkameras
  [[X]] Starker Lichteinfall


Mit welcher Technik kann man Salz-und-Pfeffer-Rauschen in einem Bild beheben bzw. entfernen?

[[Medianfilter]]

### Beispiel
Beheben wir nun in dieser Beispiel-Tabelle das Salz-und-Pfeffer-Rauschen.

"Bild" mit Salz-und-Pfeffer-Rauschen
------------------------------------

{{1}} Führe bitte folgenden Code "</>-Symbol" aus.

```html -Mit-Salz-und-Pfeffer-Rauschen.html
<head>
  <meta charset="utf-8">
    <style>
      table      {border: 10px solid red;}
      td         {border: 1px solid black; padding: 20px;}
    </style>
</head>
<body>
  <table>
    <tbody>
      <tr>
        <td>255</td>
        <td>255</td>
        <td bgcolor="#bebebe"><font color="#ffffff">190</font></td>
        <td>255</td>
        <td>255</td>
      </tr>
      <tr>
        <td>255</td>
        <td bgcolor="#000000"><font color="#ffffff">0</font></td>
        <td bgcolor="#000000"><font color="#ffffff">0</font></td>
        <td bgcolor="#888888"><font color="#ffffff">136</font></td>
        <td bgcolor="#3c3c3c"><font color="#ffffff">60</font></td>
      </tr>
      <tr>
        <td>255</td>
        <td bgcolor="#3c3c3c"><font color="#ffffff">60</font></td>
        <td bgcolor="#888888"><font color="#ffffff">136</font></td>
        <td>255</td>
        <td>255</td>
      </tr>
      <tr>
        <td>255</td>
        <td>255</td>
        <td bgcolor="#000000"><font color="#ffffff">0</font></td>
        <td bgcolor="#000000"><font color="#ffffff">0</font></td>
        <td>255</td>
      </tr>
      <tr>
        <td bgcolor="#3c3c3c"><font color="#ffffff">60</font></td>
        <td>255</td>
        <td bgcolor="#888888"><font color="#ffffff">136</font></td>
        <td>255</td>
        <td>255</td>
      </tr>
    </tbody>
  </table>
</body>
```
@WebDev.HTML


<br>

{{2}}**Wende mittels der 3x3-Rasterisierung den Medianfilter an um das Salz-und-Pfeffer-Rauschen zu entfernen.**

> * Wie man den Medianfilter verwendet, erfährst du im Video am Anfang das Kapitels.
> * Die einzelnen Pixel bzw. Kästchen haben folgende Bezeichnung:

  <table>
    <tbody>
      <tr>
        <td>A1</td>
        <td>B1</td>
        <td bgcolor="#bebebe"><font color="#ffffff">C1</font></td>
        <td>D1</td>
        <td>E1</td>
      </tr>
      <tr>
        <td>A2</td>
        <td bgcolor="#000000"><font color="#ffffff">B2</font></td>
        <td bgcolor="#000000"><font color="#ffffff">C2</font></td>
        <td bgcolor="#888888"><font color="#ffffff">D2</font></td>
        <td bgcolor="#3c3c3c"><font color="#ffffff">E2</font></td>
      </tr>
      <tr>
        <td>A3</td>
        <td bgcolor="#3c3c3c"><font color="#ffffff">B3</font></td>
        <td bgcolor="#888888"><font color="#ffffff">C3</font></td>
        <td>D3</td>
        <td>E3</td>
      </tr>
      <tr>
        <td>A4</td>
        <td>B4</td>
        <td bgcolor="#000000"><font color="#ffffff">C4</font></td>
        <td bgcolor="#000000"><font color="#ffffff">D4</font></td>
        <td>D5</td>
      </tr>
      <tr>
        <td bgcolor="#3c3c3c"><font color="#ffffff">A5</font></td>
        <td>B5</td>
        <td bgcolor="#888888"><font color="#ffffff">C5</font></td>
        <td>D5</td>
        <td>E5</td>
      </tr>
    </tbody>
  </table>

<br>

Rechner für den Medianwert
-------

{{3}} **Trage die Werte ein und lasse den Medianwert über den Button </> bestimmen.**

>Trage die neun Werte in sortierter Reihenfolge und mit Komma getrennt in die eckige Klammer.

```js +Eingabe_Medianwertrechner.js
const median = [1, 2, 3, 4, 5, 6, 7, 8, 9];
```
```js -Medianwertrechner.js
median.sort(function(a, b){return a - b});
median[4];
```
<script>
@input(0)
@input(1)
</script>

{{4}} **Trage hier die Ergebnisse ein**

Medianwert für Kästchen B2?

[[190]]

Medianwert für Kästchen C2?

[[190]]

Medianwert für Kästchen D2?

[[190]]

Medianwert für Kästchen B3?

[[190]]

Medianwert für Kästchen C3?

[[190]]

Medianwert für Kästchen D3?

[[190]]

Medianwert für Kästchen B4?

[[190]]

Medianwert für Kästchen C4?

[[190]]

Medianwert für Kästchen D4?

[[190]]


### Lösung: "Bild" ohne Salz-und-Pfeffer-Rauschen 

So sieht die Grafik mit dem Medianfilter aus. 

```html -Ohne-Salz-und-Pfeffer-Rauschen.html
<head>
  <meta charset="utf-8">
    <style>
      table      {border: 10px solid red;}
      td         {border: 1px solid black; padding: 20px;}
    </style>
</head>
<body>
  <table>
    <tbody>
      <tr>
        <td>255</td>
        <td>255</td>
        <td bgcolor="#bebebe"><font color="#ffffff">190</font></td>
        <td>255</td>
        <td>255</td>
      </tr>
      <tr>
        <td>255</td>
        <td bgcolor="#bebebe"><font color="#ffffff">190</font></td>
        <td bgcolor="#bebebe"><font color="#ffffff">190</font></td>
        <td bgcolor="#bebebe"><font color="#ffffff">190</font></td>
        <td bgcolor="#3c3c3c"><font color="#ffffff">60</font></td>
      </tr>
      <tr>
        <td>255</td>
        <td bgcolor="#bebebe"><font color="#ffffff">190</font></td>
        <td bgcolor="#bebebe"><font color="#ffffff">190</font></td>
        <td bgcolor="#bebebe"><font color="#ffffff">190</font></td>
        <td>255</td>
      </tr>
      <tr>
        <td>255</td>
        <td bgcolor="#bebebe"><font color="#ffffff">190</font></td>
        <td bgcolor="#bebebe"><font color="#ffffff">190</font></td>
        <td bgcolor="#bebebe"><font color="#ffffff">190</font></td>
        <td>255</td>
      </tr>
      <tr>
        <td bgcolor="#3c3c3c"><font color="#ffffff">60</font></td>
        <td>255</td>
        <td bgcolor="#888888"><font color="#ffffff">136</font></td>
        <td>255</td>
        <td>255</td>
      </tr>
    </tbody>
  </table>
</body>
```
@WebDev.HTML


## Gaußfilter

{{1}} Schau dir das Video an, um zu verstehen, wie der Gaußfilter funktioniert.

!?[video](https://youtu.be/ajDczVqGPkM)

Nun wollen wir das mal selber ausprobieren...

--------------

Mittelwert berechnen
---------------------------

![image](https://i.imgur.com/KyYUErZ.jpeg)

<br>


{{2}} **Auftrag: Berechne nun den Mittelwert für das Kästchen in der Mitte aus.**

>Wiederholung: Um den Mittelwert zu bestimmen, addierst du alle Graustufenwerte aus dem Bild und teilst diese durch die Anzahl der Käschten. Bitte auf eine Zahl __ohne Nachkommastelle__ runden!

```javascript +rechner.js
(1+2+3)/3
```
<script>@input</script>

Anschließend müssen wir den Graustufenwert noch in einen Farbcode umrechnen, damit wir damit weiterarbeiten können.

-----------

Graustufen in Farbcodes umrechnen
-------------------

{{3}}  **Trage in der 1. Zeile des Eingabefensters deinen erechneten Mittelwert ein, z.B.:** `let grau = 123;`

```js +eingabe.js
let grau = 123;
```
```js     -umrechner.js
let hexStr = grau.toString(16);

if (grau <= 15){
  "#"+"0"+hexStr+"0"+hexStr+"0"+hexStr;
}
else {
  "#"+hexStr+hexStr+hexStr;
}
```
<script>
@input(0)
@input(1)
</script>




Gaußfilter in 3x3-Matrix anwenden
---------------------------------

{{4}} **Trage nun in der 18. Zeile den Farbcode ein.** Beispiel: `<td bgcolor="123456"><font color="#ffffff">123</font></td>`

>bgcolor="123456" steht für "Backgroundcolor", also Hintergrundfarbe

>Das was zwischen <> und </> steht (also die "50"), ist der Text, der angezeigt werden soll. Also wenn du aus der 50 eine andere Zahl machen möchteste musst, du diese den Text zwischen den Tags anpassen.


```html +gaussfilter.html
<head>
  <meta charset="utf-8">
    <style>
      table      {border: 10px solid red;}
      td         {border: 1px solid black; padding: 20px;}
    </style>
</head>
<body>
  <table>
    <tbody>
      <tr>
        <td bgcolor="#323232"><font color="#ffffff">50</font></td>
        <td>255</td>
        <td>255</td>
      </tr>
      <tr>
        <td bgcolor="#323232"><font color="#ffffff">50</font></td>
        <td bgcolor="#323232"><font color="#ffffff">50</font></td>
        <td>255</td>
      </tr>
      <tr>
        <td bgcolor="#323232"><font color="#ffffff">50</font></td>
        <td>255</td>
        <td>255</td>
      </tr>
    </tbody>
  </table>
</body>
```
@WebDev.HTML

<br>

{{5}} Hast du die richtige Lösung?

Kopiere den Inhalt der Zeile 18 in das Lösungsfeld:

[[<td bgcolor="#a4a4a4"><font color="#ffffff">164</font></td>]]



### Quiz Gaußfilter

{{1}} **Beantworte nun die Fragen.**

Was ist der Medianwert?

 [(X)] Der Wert, der in der Mitte der Datenverteilung liegt.
 [( )] Der erechnetet Wert, der den Durschnitt der Daten bildet.
 [( )] Das arithmetische Mittel.


Was ist der Mittelwert?

 [[ ]] Der Wert, der in der Mitte der Datenverteilung liegt.
 [[X]] Der erechnetet Wert, der den Durschnitt der Daten bildet.
 [[X]] Das arithmetische Mittel.

Mit welcher Technik kann man Salz-und-Pfeffer-Rauschen in einem Bild beheben bzw. entfernen?

[[Medianfilter]]

Mit welcher Technik kann man Farbunterschiede in Bildern glätten?

[[Gaußfilter]]



### Beispiel

Beispiel in einem größeren Maßstab
----------------------------------

![image](https://th.bing.com/th/id/OIP.BLP5w5SBsxj77fHKB1QhVgAAAA?pid=ImgDet&rs=1)

<br>

Jetzt wollen wir das mal selber ausprobieren...

"Bild" mit Salz-und-Pfeffer-Rauschen
------------------------------------

```html -Mit-Salz-und-Pfeffer-Rauschen.html
<head>
  <meta charset="utf-8">
    <style>
      table      {border: 10px solid red;}
      td         {border: 1px solid black; padding: 20px;}
    </style>
</head>
<body>
  <table>
    <tbody>
      <tr>
        <td>255</td>
        <td>255</td>
        <td bgcolor="#bebebe"><font color="#ffffff">190</font></td>
        <td>255</td>
        <td>255</td>
      </tr>
      <tr>
        <td>255</td>
        <td bgcolor="#000000"><font color="#ffffff">0</font></td>
        <td bgcolor="#000000"><font color="#ffffff">0</font></td>
        <td bgcolor="#888888"><font color="#ffffff">136</font></td>
        <td bgcolor="#3c3c3c"><font color="#ffffff">60</font></td>
      </tr>
      <tr>
        <td>255</td>
        <td bgcolor="#3c3c3c"><font color="#ffffff">60</font></td>
        <td bgcolor="#888888"><font color="#ffffff">136</font></td>
        <td>255</td>
        <td>255</td>
      </tr>
      <tr>
        <td>255</td>
        <td>255</td>
        <td bgcolor="#000000"><font color="#ffffff">0</font></td>
        <td bgcolor="#000000"><font color="#ffffff">0</font></td>
        <td>255</td>
      </tr>
      <tr>
        <td bgcolor="#3c3c3c"><font color="#ffffff">60</font></td>
        <td>255</td>
        <td bgcolor="#888888"><font color="#ffffff">136</font></td>
        <td>255</td>
        <td>255</td>
      </tr>
    </tbody>
  </table>
</body>
```
@WebDev.HTML

<br>

{{1}} **Arbeitsauftrag: Wende mittels der 3x3-Rasterisierung den Gaußfilter an.**

> * Wie man den Gaußfilterfilter verwendet, erfährst du im Video am Anfang das Kapitels.
> * Die einzelnen Pixel bzw. Kästchen haben folgende Bezeichnung:

  <table>
    <tbody>
      <tr>
        <td>A1</td>
        <td>B1</td>
        <td bgcolor="#bebebe"><font color="#ffffff">C1</font></td>
        <td>D1</td>
        <td>E1</td>
      </tr>
      <tr>
        <td>A2</td>
        <td bgcolor="#000000"><font color="#ffffff">B2</font></td>
        <td bgcolor="#000000"><font color="#ffffff">C2</font></td>
        <td bgcolor="#888888"><font color="#ffffff">D2</font></td>
        <td bgcolor="#3c3c3c"><font color="#ffffff">E2</font></td>
      </tr>
      <tr>
        <td>A3</td>
        <td bgcolor="#3c3c3c"><font color="#ffffff">B3</font></td>
        <td bgcolor="#888888"><font color="#ffffff">C3</font></td>
        <td>D3</td>
        <td>E3</td>
      </tr>
      <tr>
        <td>A4</td>
        <td>B4</td>
        <td bgcolor="#000000"><font color="#ffffff">C4</font></td>
        <td bgcolor="#000000"><font color="#ffffff">D4</font></td>
        <td>D5</td>
      </tr>
      <tr>
        <td bgcolor="#3c3c3c"><font color="#ffffff">A5</font></td>
        <td>B5</td>
        <td bgcolor="#888888"><font color="#ffffff">C5</font></td>
        <td>D5</td>
        <td>E5</td>
      </tr>
    </tbody>
  </table>

<br>

{{2}} **Berechne mittels des Rechners die Gaußwerte und runde sie ohne Nachkommastelle.**

```javascript +rechner.js
(1+2+3)/3
```
<script>@input</script>


{{3}} **Trage hier die Ergebnisse ein**

Medianwert für Kästchen B2?

[[156]]

Medianwert für Kästchen C2?

[[160]]

Medianwert für Kästchen D2?

[[189]]

Medianwert für Kästchen B3?

[[170]]

Medianwert für Kästchen C3?

[[147]]

Medianwert für Kästchen D3?

[[147]]

Medianwert für Kästchen B4?

[[170]]

Medianwert für Kästchen C4?

[[142]]

Medianwert für Kästchen D4?

[[177]]

### Lösung: "Bild" mit Gaußfilter geglättet 


```html -geglaettet.html
<head>
  <meta charset="utf-8">
    <style>
      table      {border: 10px solid red;}
      td         {border: 1px solid black; padding: 20px;}
    </style>
</head>
<body>
  <table>
    <tbody>
      <tr>
        <td>255</td>
        <td>255</td>
        <td bgcolor="#bebebe"><font color="#ffffff">190</font></td>
        <td>255</td>
        <td>255</td>
      </tr>
      <tr>
        <td>255</td>
        <td bgcolor="#9c9c9c"><font color="#ffffff">156</font></td>
        <td bgcolor="#a0a0a0"><font color="#ffffff">160</font></td>
        <td bgcolor="#bdbdbd"><font color="#ffffff">189</font></td>
        <td bgcolor="#3c3c3c"><font color="#ffffff">60</font></td>
      </tr>
      <tr>
        <td>255</td>
        <td bgcolor="#aaaaaa"><font color="#ffffff">170</font></td>
        <td bgcolor="#939393"><font color="#ffffff">147</font></td>
        <td bgcolor="#939393"><font color="#ffffff">147</font></td>
        <td>255</td>
      </tr>
      <tr>
        <td>255</td>
        <td bgcolor="#aaaaaa"><font color="#ffffff">170</font></td>
        <td bgcolor="#8e8e8e"><font color="#ffffff">142</font></td>
        <td bgcolor="#b1b1b1"><font color="#ffffff">177</font></td>
        <td>255</td>
      </tr>
      <tr>
        <td bgcolor="#3c3c3c"><font color="#ffffff">60</font></td>
        <td>255</td>
        <td bgcolor="#888888"><font color="#ffffff">136</font></td>
        <td>255</td>
        <td>255</td>
      </tr>
    </tbody>
  </table>
</body>
```
@WebDev.HTML