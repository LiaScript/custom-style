<!--
author:   André Dietrich

email:    LiaScript@web.de

version:  1.0.0

language: en

narrator: US English Male

comment:  A simple demo that shows, how custom styles can be applied to a
          LiaScript document...


link:     https://cdn.jsdelivr.net/chartist.js/latest/chartist.min.css

script:   https://cdn.jsdelivr.net/chartist.js/latest/chartist.min.js

link:     custom.css
          https://fonts.googleapis.com/css?family=Abril Fatface
-->


# Custom-Style demo


This is a simple demo, that shows how LiaScript courses can be customized.

Please see the [Lia-Script-Version](https://liascript.github.io/course/?https://raw.githubusercontent.com/liaScript/custom-style/master/README.md)
to see how this document gets rendered in [LiaScript](https://liascript.github.io).

## How does it work?

You can load any css file that you want, simply place the URL of your style
into the main header of your document via `link: url.css`. Unfortunately loading
`custom.css` directly does work only for local development, using it on github
you will need a CDN, such as https://www.jsdelivr.com/?docs=gh ... simply refer
to your style in your github repository.



``` markdown README.md
<!--
author:   André Dietrich
email:    LiaScript@web.de
version:  0.0.1
language: en
narrator: US English Male
link:     https://cdn.jsdelivr.net/gh/liascript/custom-style/custom.css
          https://fonts.googleapis.com/css?family=Abril Fatface
```

Actually you can overwrite every peace of LiaScript style, simply by changing
one of the `lia-` classes... Unfortunately, you will have to put an `!important`
to every css attribute in order to force its usage. Thus, if you do not change
the color, you can still switch between the LiaScript color schemes, otherwise
there will only one color config available...

``` css  custom.css
:root {
  --main-bg-color: #FF0000;
}

body {
  font-family: 'Abril Fatface', sans-serif !important;
}

h1.lia-h1 {
  font-size:5vw !important;
  margin-left:auto !important;
  margin-right:auto !important;
}

.lia-slide .lia-toolbar {
  background: var(--main-bg-color) !important;
  background-image: url("https://liascript.github.io/course/logo_192.c4a21617.png") !important;
  background-size: contain !important;
  background-repeat: no-repeat !important;
  background-position: center !important;
}

.lia-toc .lia-toolbar {
  background: var(--main-bg-color) !important;
}

.lia-btn {
  background: var(--main-bg-color) !important;
}

.lia-input {
  background: var(--main-bg-color) !important;
}

.lia-active {
  background: var(--main-bg-color) !important;
}

.lia-quote {
  background: var(--main-bg-color) !important;
  border-left-color: #990000 !important;
  color: #FFFFFF !important
}

.lia-accordion {
  background: var(--main-bg-color) !important;
  font-size: 12px !important;
}

.lia-accordion-dummy {
  background: var(--main-bg-color) !important;
  font-size: 12px !important;
}

.lia-quiz {
  border-color: var(--main-bg-color) !important;
}

.lia-link {
  color: #00FF00 !important
}
```

# Some Demo Stuff


## Markdown

You can use common [Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) syntax to create your course, such as:

1. Lists
2. ordered or

   * unordered
   * ones ...


| Header 1   | Header 2   |
| :--------- | :--------- |
| Item 1     | Item 2     |


Images:

![images](https://farm2.static.flickr.com/1618/26701766821_7bea494826.jpg)

> some simple notes

### Extensions

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


### Styling

<!-- class = "animated rollIn" style = "animation-delay: 2s; color: purple" -->
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


### Projects

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

## More

Find out what you can even do more with quizzes:

https://liascript.github.io/course/?https://raw.githubusercontent.com/liaScript/docs/master/README.md
