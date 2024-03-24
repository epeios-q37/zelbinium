---
title: "Inspiration"
menu: "Inspiration"
weight: 3
bookCollapseSection: false
---

# Inspiration

Here are a few applications, some of which allow users to interact with each other (two-panel preview). All these applications are grouped together in the repository at <https://github.com/epeios-q37/zelbinium>. The term in brackets is the name of the folder in which the source code for each application is located.

Clicking on an application's preview gives you access to its *repl*, from which the application can be [launched](../action/launch), [shared](../action/share), [explored](../action/explore), [modified](../action/modify) and used as inspiration to [create](../action/create) your own applications, as detailed in the [*Action!*](../action/) section.

Clicking on *Code* displays the application's source code. An application can have more than one source file, which can be displayed from its *repl*.

## *Hello, World!* (`Hello`)

[*Hello, World!*](https://en.wikipedia.org/wiki/%22Hello,_World!%22_program) program showing the basics of a *Zelbinium* application. The application simply displays a message showing the contents of a text field.

<div data-demo="Hello"></div>

## *Hello, World!* shared (`Hellos`)

Same application as above, but messages are displayed to all users. Shows the basics of an application that allows users to interact.

<div data-demo="Hellos"></div>

## *Messages* (`Messages`)

This is the application used in the [*Action!*](../action/) section. It allows messages to be exchanged between all devices connected to the same application.

<div data-demo="Messages"></div>

## *Widgets* (`Widgets`)

This application shows an example of use of commonly used graphical interface components ([*widgets*](https://en.wikipedia.org/wiki/Graphical_widget)) and the corresponding source code (*HTML* and *Python*).

<div data-demo="Widgets"></div>

## *Connect Four* (`FourInARow`)

The [*Connect Four*](https://en.wikipedia.org/wiki/Connect_Four) game.

<div data-demo="FourInARow"></div>

## *Mancala* (`Mancala`)

The ancient two-player, seed-sowing game.

Grab the seeds from a pit on your side and place one in each following pit, going counterclockwise and skipping your opponent's store. If your last seed lands in an empty pit of yours, move the opposite pit's seeds into your store. The goal is to get the most seeds in your store on the side of the board. If the last placed seed is in your store, you get a free turn.

<div data-demo="Mancala"></div>

## *Flood it!* (`Flooder`)

Set the upper left color/shape, which fills in all the adjacent squares of that color/shape, by selecting a square with the desired color/shape. Try to make the entire board the same color/shape.

<div data-demo="Flooder"></div>

<!--

## *Blackjack* (`Blackjack`)

The classic card game also known as 21 (This version doesn't have splitting or insurance).

<div data-demo="Blackjack"></div>

-->

## *Pig game* (`PigGame`)

A multi-player version of the [Pig game](https://en.wikipedia.org/wiki/Pig_(dice_game)#Gameplay).

<div data-demo="PigGame"></div>


<!-- -->

<style>
  details {
    padding: 1rem 0.3rem !important;
  }
  pre {
    word-wrap: break-word;
    white-space: break-spaces;
    font-size: small;
    line-height: normal;
    padding: 1rem 0.4rem !important;
    height: 500px;
  }
  summary:focus {
    outline-style: none;
  }
</style>

<script>
  function demoInsert(element)
  {
    const demo = element.getAttribute("data-demo");
    element.innerHTML = '\
<center>\
  <div>\
    <img onclick="this.parentElement.parentElement.nextElementSibling.open=\'true\'" style="cursor: pointer; padding: 10px; margin: 10px 0 0 0; box-shadow: rgba(0, 0, 0, 0.3) 0px 19px 38px, rgba(0, 0, 0, 0.22) 0px 15px 12px; border-radius: 10px;" src="./' + demo +  '.gif"/>\
  </div>\
</center>\
<details ontoggle="demoFill(\'' + demo + '\');this.removeAttribute(\'ontoggle\');this.scrollIntoView();">\
  <summary>Hide/show</summary>\
  <iframe allow="web-share" id="' + demo + '-code" style="width: 100%;height: 90vh;" src="data:text/html;charset=utf-8,<center><h3>Please wait…</h3></center>">\
  </iframe>\
  <span>\
    Click <a target="_blank" href="https://faas.q37.info/brython?demo=' + demo + '">here</a> to open this application in its own page.\
  </span>\
</details>';
  }

  function demoFill(demo) {
    document.getElementById(demo + '-code').src="https://faas.q37.info/brython?demo=" + demo;
  }

  const demos = document.getElementsByTagName("div");

  for ( const demo of demos ) {
    if ( demo.hasAttribute("data-demo") ) {
      demoInsert(demo);
    }
  }
</script>