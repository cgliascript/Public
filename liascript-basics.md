<!--
author:   Florian Schroers

email:    fschroers@uni-koblenz.de

version:  1.0.0

language: de

narrator: Deutsch Male

logo:     https://liascript.github.io/img/bg-showcase-1.jpg

comment:  Dies ist ein kleiner Kurs zum Vorstellen von LiaScript.

link:     https://cdn.jsdelivr.net/chartist.js/latest/chartist.min.css

script: https://cdn.jsdelivr.net/chartist.js/latest/chartist.min.js
script: https://cdn.rawgit.com/davidedc/Algebrite/master/dist/algebrite.bundle-for-browser.js


import:   https://raw.githubusercontent.com/liaScript/rextester_template/master/README.md
          https://github.com/LiaTemplates/KekuleJS
          https://github.com/LiaTemplates/VTK
          https://github.com/LiaTemplates/Algebrite
          https://github.com/LiaTemplates/ProcessingJS
          https://github.com/LiaTemplates/mec2/blob/main/README.md



-->

# LiaScript - Basic Documentation

# Inhalt und Ziel dieses Vorstellungskurses

1. Was ist LiaScript?
2. Welche grundlegenden (technchnischen) Möglichkeiten bietet LiaScript?
3. Ausblick
4. Diskusionsfrage: Könnte man useren (hypotetischen) Online-Kurs komplett in LiaScript implementieren und so veröffentlichen, dass dieser an einer Schule im Unterricht durchgeführt werden kann?

# Was ist LiaScript?

![images](https://avatars.githubusercontent.com/u/32539316?s=200&v=4)

* Es ist eine auf Markdown basierende Scriptsprache für interaktive Kurse und datengesteuertes Publizieren

* Es ist in JavaScript implementiert und läuft direkt im Browser

 * Der Interpreter selbst ist auch ein Lesegerät, der es ermöglicht Dokumente sowie den Fortschritt zu speichern

* Kurse können auch offline besucht werden, da der Interpreter auch eine progressive Web-App (PWA) ist, die es ermöglicht, Dokumente zu speichern und direkt im Browser (lokal) fortzuführen

* Es ist privat, LiaScript/Markdown speichert weder Daten über die Kurse, noch über die Nutzer und deren Fortschritte

[preview-lia](https://raw.githubusercontent.com/LiaScript/docs/master/README.md)

## Was ist Markdown?

![images](https://www.fullstackpython.com/img/logos/markdown.png)

Markdown ist eine **vereinfachte Auszeichnungssprache**, die von John Gruber und Aaron Swartz entworfen und im Dezember 2004 mit Version 1.0.1 spezifiziert wurde. Ein Ziel von Markdown ist eine **leicht lesbare Ausgangsform** bereits vor der Konvertierung. Als Auszeichnungselemente wurden daher vor allem Auszeichnungsarten verwendet, die in Plain text und E-Mails üblich sind. Auch andere Auszeichnungssprachen mit ähnlichen Zielen zur Lesbarkeit – wie reStructuredText oder Textile – hatten Einfluss auf die Syntax[^1](https://de.wikipedia.org/wiki/Markdown).

# Beispiele für Formatierungen mit Markdown
Tabellen
--------
| Header 1   | Header 2   |
| :--------- | :--------- |
| Item 1     | Item 2     |
| Item 3     | Item 4     |
| Item 5     | Item 6     |

Hervorhebungen
--------------
>Wichtige Hinweise

Schriftformatierung
-------------------
*Kursiv* oder _Kursiv_

**Fett** oder __Fett__

~Durchgestrichen~

~~Unterstrichen~~

Trennstrich
-----------
-----------

Code
----
`Code oder Sonderzeichen`, die nicht vom Markdown-Interpreter behandelt werden sollen

## Extensions

     --{{0}}--
But you can also include other features such as spoken text.

      --{{1}}--
Insert any kind of audio file:

       {{1}}
?[audio](https://bigsoundbank.com/UPLOAD/mp3/1068.mp3)


     --{{2}}--
Even videos or change the language completely.

       {{2-3}}
!?[video](https://www.youtube.com/watch?v=bICfKRyKTwE)


      --{{3 Russian Female}}--
Первоначально создан в 2004 году Джоном Грубером (англ. John Gruber) и Аароном
Шварцем. Многие идеи языка были позаимствованы из существующих соглашений по
разметке текста в электронных письмах...




    {{3}}
Type "voice" to see a list of all available languages.


## Styling

<!-- class = "animated rollIn" style = "animation-delay: 2s; color: green" -->
The whole text-block should appear in purple color and with a wobbling effect.
Which is a **bad** example, please use it with caution ...
~~ only this is red ;-) ~~ <!-- class = "animated infinite bounce" style = "color: red;" -->

## Charts

Use ASCII-Art to draw diagrams:

                                    Multiline
    1.9 |    DOTS
        |                 ***
      y |               *     *
      - | r r r r r r r*r r r r*r r r r r r r
      a |             *         *
      x |            *           *
      i | B B B B B * B B B B B B * B B B B B
      s |         *                 *
        | *  * *                       * *  *
     -1 +------------------------------------
        0              x-axis               1

## UML


```` ascii
   ____[]
  | ___ |
  ||   ||  device
  ||___||  loads
  | ooo |----------------------------------------------------------.
  | ooo |    |                          |                          |
  | ooo |    |                          |                          |
  '_____'    |                          |                          |
             |                          |                          |
             v                          v                          v
   .-------------------.  .---------------------------.  .-------------------.
   | Loadable module C |  |     Loadable module A     |  | Loadable module B |
   '-------------------'  |---------------------------|  |   (instrumented)  |
             |            |         .-----.           |  '-------------------'
             '------------+-------->| A.o |           |             |
                 calls    |         '-----'           |             |
                          |    .------------------.   |             |
                          |   / A.instrumented.o /<---+-------------'
                          |  '------------------'     |    calls
                          '---------------------------'
````

## Quizzes

### A Textquiz

What did the **fish** say when he hit a **concrete wall**?

    [[dam]]

### Multiple Choice

Just add as many points as you wish:

    [[X]] Only the **X** marks the correct point.
    [[ ]] Empty ones are wrong.
    [[X]] ...

### Single Choice

Just add as many points as you wish:

    [( )] ...
    [(X)] <-- Only the **X** is allowed.
    [( )] ...

## Executable Code

A drawing example, for demonstrating that any JavaScript library can be used, also for drawing.

```javascript
// Initialize a Line chart in the container with the ID chart1
new Chartist.Line('#chart1', {
  labels: [1, 2, 3, 4],
  series: [[100, 120, 180, 200]]
});

// Initialize a Line chart in the container with the ID chart2
new Chartist.Bar('#chart2', {
  labels: [1, 2, 3, 4],
  series: [[5, 2, 8, 3]]
});
```
<script>@input</script>

<div class="ct-chart ct-golden-section" id="chart1"></div>
<div class="ct-chart ct-golden-section" id="chart2"></div>


## Projects

You can make your code executable and define projects:

``` js     -EvalScript.js
let who = data.first_name + " " + data.last_name;

if(data.online) {
  who + " is online"; }
else {
  who + " is NOT online"; }
```
``` json    +Data.json
{
  "first_name" :  "Sammy",
  "last_name"  :  "Shark",
  "online"     :  true
}
```
<script>
  // insert the JSON dataset into the local variable data
  let data = @input(1);

  // eval the script that uses this dataset
  eval(`@input(0)`);
</script>

## Programierumgebungen

Einfach mit JavaScript
----------------------

``` javascript
x + x
```
<script> Algebrite.run(`@input`) </script>

```javascript
f=sin(t)^4-2*cos(t/2)^3*sin(t)

f=circexp(f)

defint(f,t,0,2*pi)
```
<script> Algebrite.run(`@input`) </script>

### Prolog
<!--
script:   https://curiosity-driven.github.io/prolog-interpreter/parser.js
          https://curiosity-driven.github.io/prolog-interpreter/interpreter.js
-->


** Load Database and Rules: **

```prolog
exists(A, list(A, _, _, _, _)).
exists(A, list(_, A, _, _, _)).
exists(A, list(_, _, A, _, _)).
exists(A, list(_, _, _, A, _)).
exists(A, list(_, _, _, _, A)).

rightOf(R, L, list(L, R, _, _, _)).
rightOf(R, L, list(_, L, R, _, _)).
rightOf(R, L, list(_, _, L, R, _)).
rightOf(R, L, list(_, _, _, L, R)).

middle(A, list(_, _, A, _, _)).

first(A, list(A, _, _, _, _)).

nextTo(A, B, list(B, A, _, _, _)).
nextTo(A, B, list(_, B, A, _, _)).
nextTo(A, B, list(_, _, B, A, _)).
nextTo(A, B, list(_, _, _, B, A)).
nextTo(A, B, list(A, B, _, _, _)).
nextTo(A, B, list(_, A, B, _, _)).
nextTo(A, B, list(_, _, A, B, _)).
nextTo(A, B, list(_, _, _, A, B)).

puzzle(Houses) :-
  exists(house(red, english, _, _, _), Houses),
  exists(house(_, spaniard, _, _, dog), Houses),
  exists(house(green, _, coffee, _, _), Houses),
  exists(house(_, ukrainian, tea, _, _), Houses),
  rightOf(house(green, _, _, _, _), house(ivory, _, _, _, _), Houses),
  exists(house(_, _, _, oldgold, snails), Houses),
  exists(house(yellow, _, _, kools, _), Houses),
  middle(house(_, _, milk, _, _), Houses),
  first(house(_, norwegian, _, _, _), Houses),
  nextTo(house(_, _, _, chesterfield, _), house(_, _, _, _, fox), Houses),
  nextTo(house(_, _, _, kools, _),house(_, _, _, _, horse), Houses),
  exists(house(_, _, orangejuice, luckystike, _), Houses),
  exists(house(_, japanese, _, parliament, _), Houses),
  nextTo(house(_, norwegian, _, _, _), house(blue, _, _, _, _), Houses),
  exists(house(_, _, water, _, _), Houses),
  exists(house(_, _, _, _, zebra), Houses).

solution(WaterDrinker, ZebraOwner) :-
  puzzle(Houses),
  exists(house(_, WaterDrinker, water, _, _), Houses),
  exists(house(_, ZebraOwner, _, _, zebra), Houses).
```
<script>
var rules = parser(lexer(`@input`)).parseRules();
window['prolog_db'] = new Database(rules);

"database loaded";
</script>


```prolog
solution(WaterDrinker, ZebraOwner)
```
<script>
var rslt = "";

var goal = parser(lexer(`@input`)).parseTerm();

for (var item of window.prolog_db.query(goal)) {
    rslt += "Yes: " + item + "\n";
}

if (rslt === "") {
   'No';
} else {
   rslt;
}
</script>

## Visualisierung

```cpp
// Global variables
float radius = 50.0;
int X, Y;
int nX, nY;
int delay = 16;

// Setup the Processing Canvas
void setup(){
  size( 400, 200 );
  strokeWeight( 10 );
  frameRate( 15 );
  X = width / 2;
  Y = height / 2;
  nX = X;
  nY = Y;
}

// Main draw loop
void draw(){
  radius = radius + sin( frameCount / 4 );
  // Track circle to new destination
  X+=(nX-X)/delay;
  Y+=(nY-Y)/delay;
  // Fill canvas grey
  background( 100 );
  // Set fill-color to blue
  fill( 0, 121, 184 );
  // Set stroke-color white
  stroke(255);
  // Draw circle
  ellipse( X, Y, radius, radius );
}

// Set circle's next destination
void mouseMoved(){
  nX = mouseX;
  nY = mouseY;
}
```
@Processing.eval



## Weitere Tools von LiaScript

LiveEditor
----------
This is a browser-based collaborative online editor for LiaScript. All content is stored within your browser. Collaboration is enabled by WebRTC and Yjs. The snippets are already included, simply type "lia" to explore some features of LiaScript. By the way, if you have a GitHub account, you can directly export your courses to gists.

liascript-devserver
-------------------
If you prefer another editor or if you have a couple of courses that you want to test locally, then you should try out this open-source project...

liascript-exporter
------------------
This project allows to pack your entire course into a SCORM compliant format and thus to upload your LiaScript courses to the most common Learning Management Systems (LMS).

--------------------------------------------------
Alles hier zu finden: https://liascript.github.io/

# Diskusionsfrage:
Könnte man useren (hypotetischen) Online-Kurs komplett in LiaScript implementieren und so veröffentlichen, dass dieser an einer Schule im Unterricht durchgeführt werden kann?
