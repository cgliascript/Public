<!--
author:   Florian Schroers

email:    fschroers@uni-koblenz.de

version:  1.0.0

language: de

narrator: Deutsch Male

logo:     https://i.imgur.com/yscy5JX.png

comment:  LiaScript-Kurs zum Kennenlernen von Filtern in der Bildbearbeitung mit Farbtönen

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

# 4. RGB-Filter

![image](https://i.imgur.com/yscy5JX.png) 
Guten Tag. Schön, dass du diesen Kurs besuchst. Ein paar Anmerkungen bevor wir loslegen. Im Unteren Bildbereich kannst du dich über die Pfeiltasten vor und zurück im Kurs bewegen. Du kannst auch dafür das Menü auf der linken Seite verwenden.

Immer wenn das der Button mit dem Zeichen </> erscheint, handelt es sich im Programmcode der ausgeführt werden kann. Klicke dann immer auf das Symbol und es passiert etwas.

>Wichtige Anmerkungen und Tipps werden so angezeigt.

Dann mal los und viel Spaß!

## Was ist RGB?

{{1}} **Schaue dir zunächst dieses  Video an.**

!?[video](https://youtu.be/-OhxD9-OZgA)

<br>

------------------------------------------------

QUIZ
----

{{2}} **Beantworte nun die Fragen.**

Wofür steht das "R" in RGB?

[[Rot]]

Wofür steht das "G" in RGB?

[[Grün]]

Wofür steht das "B" in RGB?

[[Blau]]

---------------------------------------------------------------

{{3}} **Welche Farbtöne erhält man, wenn man folgende RGB-Werte verwendet? Lösung bitte als Wort eintragen (z.B. schwarz)**

??[Farbmischer](https://informatik.schule.de/rgb/RGB_farbmischer.html)

1) 255, 0 ,255

[[violet]]

2) 0, 255, 255

[[türkis]]

3) 255, 150, 0

[[orange]]

4) 112, 112, 112

[[grau]]

## Wiederholung Filter

Filter-Maske:
-------------
> * betrachtet einen Ausschnitt einer Pixelgrafik
> * jeder Filter hat andere Vorgehensweise, wie mit Werten gearbeitet wird
> * wird über die gesamte Grafik verschoben, sodass jeder Pixel verarbeitet wird
> * je nach Vorgehensweise unterschiedliche Effekte (z.B.: Weichzeichnen, Fehlerkorrektur)

Medianfilter:
-------------
> * Median der Werte in der Filter-Maske bestimmen
> * Werte der Filter-Maske aufsteigend sortieren und Wert in der Mitte der Liste auswählen
> * mittleres Pixel der Filter-Maske nimmt Wert des Medians an
> * kann Salz-und-Pfeffer-Rauschen korrigieren

Salz-und-Pfeffer-Rauschen:
--------------------------
> * Störfaktor in Pixelgrafiken
> * zufällige Pixel nehmen Wert 0 ( = schwarz) oder 255 (=weiß) an
> * kann durch Medianfilter korrigiert werden
> * kann z.B. durch Staubartikel auf der Linse, fehlerhaften Sensoren oder starkem Lichteinfall entstehen

Gauß-Filter:
------------
> * Mittelwert der Werte der Filter-Maske bestimmen
> * alle Werte der Filter-Maske addieren und durch die Anzahl der Werte dividieren
> * mittleres Pixel nimmt Mittelwert an
> * Effekt: Weichzeichner




## Medianfilter mit RGB-Werten

{{1}} **Schaue dir zunächst dieses  Video an.**

!?[video](https://youtu.be/vHI2xUd8K2U)

<br>

---------------------------------------

Unser Ausgangsbild
--------------------------

```html -MedianfilterRGB.html
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
        <td bgcolor="#e93740"><font color="#ffffff">R 233<br>G 55<br>B 64</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
        <td bgcolor="#df414a"><font color="#ffffff">R 223<br>G 65<br>B 74</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
        <td bgcolor="#d54b36"><font color="#ffffff">R 213<br>G 75<br>B 54</font></td>
      </tr>
      <tr>
        <td bgcolor="#a35f68"><font color="#ffffff">R 163<br>G 95<br>B 104</font></td>
        <td bgcolor="#000000"><font color="#ffffff">R 0<br>G 0<br>B 0</font></td>
        <td bgcolor="#e95540"><font color="#ffffff">R 223<br>G 85<br>B 64</font></td>
        <td bgcolor="#ffffff"><font color="#000000">R 255<br>G 255<br>B 255</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
      </tr>
      <tr>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
        <td bgcolor="#e96940"><font color="#ffffff">R 233<br>G 105<br>B 64</font></td>
        <td bgcolor="#ffffff"><font color="#000000">R 255<br>G 255<br>B 255</font></td>
        <td bgcolor="#000000"><font color="#ffffff">R 0<br>G 0<br>B 0</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
      </tr>
      <tr>
        <td bgcolor="#ad7322"><font color="#ffffff">R 173<br>G 115<br>B 34</font></td>
        <td bgcolor="#ffffff"><font color="#000000">R 255<br>G 255<br>B 255</font></td>
        <td bgcolor="#000000"><font color="#ffffff">R 0<br>G 0<br>B 0</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
        <td bgcolor="#cb7d54"><font color="#ffffff">R 203<br>G 125<br>B 84</font></td>
      </tr>
      <tr>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
        <td bgcolor="#b7875e"><font color="#ffffff">R 183<br>G 135<br>B 94</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
        <td bgcolor="#c1912c"><font color="#ffffff">R 193<br>G 145<br>B 44</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
      </tr>
    </tbody>
  </table>
</body>
```
@WebDev.HTML

<br>

{{2}} **Wende den Medianfilter auf die Tabelle an.**

> Tipp: Du kannst das Tool "RGB-Bildanzeige" unten verwenden um dir die Grafik bearbeiten. Du musst nur die RGB-Werte, die in der Grafik untereinander stehen, in einer Zeile mit Komma getrennt schreiben.

````ascii
.-----.
|R 000|         .-----------.
|G 111|  ---->  |OOO,111,222|
|B 222|         .-----------.
.-----.
````

{{3}} **Berechne die Werte für den Medianfilter**

>Wende wieder die 3x3-Matrix an und berechne den Wert für R, G, und B. Du kannst den folgenden Rechner verwenden, indem du die sortierten Werte für die jeweilige Farbe in die eckigen Klammern schreibst.

```js +Eingabe_Medianwertrechner.js
const rot = [1, 2, 3, 4, 5, 6, 7, 8, 9];
const gruen = [1, 2, 3, 4, 5, 6, 7, 8, 9];
const blau = [1, 2, 3, 4, 5, 6, 7, 8, 9];
```
```js -Medianwertrechner.js
rot.sort(function(a, b){return a - b});
gruen.sort(function(a, b){return a - b});
blau.sort(function(a, b){return a - b});

const ergebnis = rot[4]+","+gruen[4]+","+blau[4];

ergebnis;
```
<script>
@input(0)
@input(1)
</script>

??[RGB-Bildanzeige](https://informatik.schule.de/rgb/RGB_bildanzeige.html?breite=5&hoehe=5)

<br>

{{4}} Überprüfe, ob du im Kästchen ganz in der Mitte alles richtig eingetragen hast:

Gib zum Beispiel folgendes ein: 123,123,123

[[223,157,237]]

### Lösung RGB-Medianfilter

```html -LoesungMedianfilterRGB.html
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
        <td bgcolor="#e93740"><font color="#ffffff">R 233<br>G 55<br>B 64</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
        <td bgcolor="#df414a"><font color="#ffffff">R 223<br>G 65<br>B 74</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
        <td bgcolor="#d54b36"><font color="#ffffff">R 213<br>G 75<br>B 54</font></td>
      </tr>
      <tr>
        <td bgcolor="#a35f68"><font color="#ffffff">R 163<br>G 95<br>B 104</font></td>
        <td bgcolor="#df5f4a"><font color="#ffffff">R 223<br>G 95<br>B 74</font></td>
        <td bgcolor="#df9ded"><font color="#ffffff">R 223<br>G 157<br>B 237</font></td>
        <td bgcolor="#d59ded"><font color="#ffffff">R 213<br>G 157<br>B 255</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
      </tr>
      <tr>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
        <td bgcolor="#df7368"><font color="#ffffff">R 233<br>G 115<br>B 104</font></td>
        <td bgcolor="#df9ded"><font color="#ffffff">R 223<br>G 157<br>B 237</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
      </tr>
      <tr>
        <td bgcolor="#ad7322"><font color="#ffffff">R 173<br>G 115<br>B 34</font></td>
        <td bgcolor="#ad9ded"><font color="#ffffff">R 173<br>G 157<br>B 237</font></td>
        <td bgcolor="#ad9ded"><font color="#ffffff">R 173<br>G 157<br>B 237</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
        <td bgcolor="#cb7d54"><font color="#ffffff">R 203<br>G 125<br>B 84</font></td>
      </tr>
      <tr>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
        <td bgcolor="#b7875e"><font color="#ffffff">R 183<br>G 135<br>B 94</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
        <td bgcolor="#c1912c"><font color="#ffffff">R 193<br>G 145<br>B 44</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
      </tr>
    </tbody>
  </table>
</body>
```
@WebDev.HTML

## Gaußfilter mit RGB-Werten

Unser Ausgangsbild
--------------------------

```html -GaussfilterRGB.html
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
        <td bgcolor="#e93740"><font color="#ffffff">R 233<br>G 55<br>B 64</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
        <td bgcolor="#df414a"><font color="#ffffff">R 223<br>G 65<br>B 74</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 169<br>G 157<br>B 237</font></td>
        <td bgcolor="#d54b36"><font color="#ffffff">R 213<br>G 75<br>B 54</font></td>
      </tr>
      <tr>
        <td bgcolor="#a35f68"><font color="#ffffff">R 163<br>G 95<br>B 104</font></td>
        <td bgcolor="#7bd617"><font color="#ffffff">R 123<br>G 214<br>B 23</font></td>
        <td bgcolor="#cb5540"><font color="#ffffff">R 203<br>G 85<br>B 64</font></td>
        <td bgcolor="#371986"><font color="#ffffff">R 55<br>G 25<br>B 134</font></td>
        <td bgcolor="#6daff2"><font color="#ffffff">R 109<br>G 175<br>B 242</font></td>
      </tr>
      <tr>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
        <td bgcolor="#e96940"><font color="#ffffff">R 233<br>G 105<br>B 64</font></td>
        <td bgcolor="#ffffff"><font color="#000000">R 255<br>G 255<br>B 255</font></td>
        <td bgcolor="#7bd617"><font color="#ffffff">R 123<br>G 214<br>B 23</font></td>
        <td bgcolor="#44d689"><font color="#ffffff">R 68<br>G 230<br>B 137</font></td>
      </tr>
      <tr>
        <td bgcolor="#ad7322"><font color="#ffffff">R 173<br>G 115<br>B 34</font></td>
        <td bgcolor="#6daff2"><font color="#ffffff">R 109<br>G 175<br>B 242</font></td>
        <td bgcolor="#7bd617"><font color="#ffffff">R 123<br>G 214<br>B 23</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
        <td bgcolor="#cb7d54"><font color="#ffffff">R 203<br>G 125<br>B 84</font></td>
      </tr>
      <tr>
        <td bgcolor="#83111b"><font color="#ffffff">R 131<br>G 17<br>B 27</font></td>
        <td bgcolor="#b7875e"><font color="#ffffff">R 183<br>G 135<br>B 94</font></td>
        <td bgcolor="#de0f17"><font color="#ffffff">R 222<br>G 15<br>B 23</font></td>
        <td bgcolor="#c1912c"><font color="#ffffff">R 193<br>G 145<br>B 44</font></td>
        <td bgcolor="#6f3925"><font color="#ffffff">R 111<br>G 57<br>B 37</font></td>
      </tr>
    </tbody>
  </table>
</body>
```
@WebDev.HTML

<br>

{{1}} **Wende den Gaußfilter auf die Tabelle an.**

> Tipp: Du kannst das Tool "RGB-Bildanzeige" unten verwenden um dir die Grafik bearbeiten. Du musst nur die RGB-Werte, die in der Grafik untereinander stehen, in einer Zeile mit Komma getrennt schreiben.

````ascii
.-----.
|R 000|         .-----------.
|G 111|  ---->  |OOO,111,222|
|B 222|         .-----------.
.-----.
````

{{3}} **Berechne die Werte für den Gaußfilter**

>Wende wieder die 3x3-Matrix an und berechne den Wert für R, G, und B. Du kannst wieder den folgenden Rechner verwenden, um die Werte zuberechnen.

```javascript +rechner.js
(1+2+3)/3
```
<script>@input</script>

??[RGB-Bildanzeige](https://informatik.schule.de/rgb/RGB_bildanzeige.html?breite=5&hoehe=5)

<br>

{{4}} Überprüfe, ob du im Kästchen ganz in der Mitte alles richtig eingetragen hast:

Gib zum Beispiel folgendes ein: 123,123,123

[[148,176,146]]

### Lösung RGB-Gaußfilter

```html -LoesungGaussfilterRGB.html
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
        <td bgcolor="#e93740"><font color="#ffffff">R 233<br>G 55<br>B 64</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
        <td bgcolor="#df414a"><font color="#ffffff">R 223<br>G 65<br>B 74</font></td>
        <td bgcolor="#459ded"><font color="#ffffff">R 169<br>G 157<br>B 237</font></td>
        <td bgcolor="#d54b36"><font color="#ffffff">R 213<br>G 75<br>B 54</font></td>
      </tr>
      <tr>
        <td bgcolor="#a35f68"><font color="#ffffff">R 163<br>G 95<br>B 104</font></td>
        <td bgcolor="#ae847c"><font color="#ffffff">R 174<br>G 132<br>B 124</font></td>
        <td bgcolor="#a38587"><font color="#ffffff">R 163<br>G 133<br>B 135</font></td>
        <td bgcolor="#99948f"><font color="#ffffff">R 153<br>G 148<br>B 143</font></td>
        <td bgcolor="#6daff2"><font color="#ffffff">R 109<br>G 175<br>B 242</font></td>
      </tr>
      <tr>
        <td bgcolor="#459ded"><font color="#ffffff">R 69<br>G 157<br>B 237</font></td>
        <td bgcolor="#a29987"><font color="#ffffff">R 162<br>G 153<br>B 135</font></td>
        <td bgcolor="#94b092"><font color="#ffffff">R 148<br>G 176<br>B 146</font></td>
        <td bgcolor="#81af82"><font color="#ffffff">R 129<br>G 175<br>B 130</font></td>
        <td bgcolor="#44d689"><font color="#ffffff">R 68<br>G 230<br>B 137</font></td>
      </tr>
      <tr>
        <td bgcolor="#ad7322"><font color="#ffffff">R 173<br>G 115<br>B 34</font></td>
        <td bgcolor="#93816a"><font color="#ffffff">R 147<br>G 129<br>B 106</font></td>
        <td bgcolor="#99f468"><font color="#ffffff">R 153<br>G 244<br>B 104</font></td>
        <td bgcolor="#9b9369"><font color="#ffffff">R 155<br>G 147<br>B 105</font></td>
        <td bgcolor="#cb7d54"><font color="#ffffff">R 203<br>G 125<br>B 84</font></td>
      </tr>
      <tr>
        <td bgcolor="#83111b"><font color="#ffffff">R 131<br>G 17<br>B 27</font></td>
        <td bgcolor="#b7875e"><font color="#ffffff">R 183<br>G 135<br>B 94</font></td>
        <td bgcolor="#de0f17"><font color="#ffffff">R 222<br>G 15<br>B 23</font></td>
        <td bgcolor="#c1912c"><font color="#ffffff">R 193<br>G 145<br>B 44</font></td>
        <td bgcolor="#6f3925"><font color="#ffffff">R 111<br>G 57<br>B 37</font></td>
      </tr>
    </tbody>
  </table>
</body>
```
@WebDev.HTML

##  Jetzt darfst du selber loslegen
 Gehe auf die Seite https://pixlr.com/de/ und probiere die Gaußfilter (Weichzeichnen) aus. Diese Funktion findet ihr unter Retuschieren.