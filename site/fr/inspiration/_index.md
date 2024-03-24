---
title: "Inspiration"
menu: "Inspiration"
weight: 3
bookCollapseSection: false
---

# Inspiration

Voici quelques applications dont certaines permettent aux utilisateurs d'interagir entre eux (prévisualisation avec deux panneaux).  L'ensemble de ces applications sont regroupées dans le dépôt à l'adresse <https://github.com/epeios-q37/zelbinium>. Le terme entre parenthèses est le nom du dossier dans lequel se situe le code source de chaque application.

En cliquant *Afficher/masquer* sous l'aperçu d'une application, vous aurez accès à son encart à partir duquel l'application pourra être lancée, partagée, explorée, modifiée <!--et servir d'inspiration pour créer ses propres applications!--> comme détaillé dans la section [*Action !*](../action/).

## *Hello world* (`Hello`)

Programme de type [*Hello world*](https://fr.wikipedia.org/wiki/Hello_world) montrant les bases d'une application *Zelbinium*. L'application affiche simplement un message reprenant le contenu d'un champ texte.

<div data-demo="Hello"></div>

## *Hello world* partagé (`Hellos`)

Même application que précédemment, mais les messages sont affichés à tous les utilisateurs. Montre les bases d'une application permettant à ses utilisateurs d'interagir.

<div data-demo="Hellos"></div>

## *Messages* (`Messages`)

Il s'agit de l'application utilisée dans la section [*Action !*](../action/). Elle permet l'échange de messages entre tous les appareils connectés à la même application.

<div data-demo="Messages"></div>

## *Widgets* (`Widgets`)

Cette application montre un exemple d'utilisation de composants d'interface graphique ([*widgets*](https://fr.wikipedia.org/wiki/Composant_d%27interface_graphique)) couramment utilisés et le code source (*HTML* et *Python*) correspondant.

<div data-demo="Widgets"></div>

## *Puissance 4* (`FourInARow`)

Le jeu [*Puissance 4*](https://fr.wikipedia.org/wiki/Puissance_4).

<div data-demo="FourInARow"></div>

## *Mancala* (`Mancala`)

Un ancien jeu de semis à deux joueurs de type [*mancala*](https://fr.wikipedia.org/wiki/Mancala).

Prenez les graines dans un emplacement de votre côté et placez-en une dans chaque emplacement suivant, dans le sens inverse des aiguilles d'une montre et en sautant la réserve de votre adversaire. Si votre dernière graine atterrit dans un emplacement vide, déplacez les graines de l'emplacement opposé dans votre réserve. Le but est d'obtenir le plus grand nombre de graines dans votre réserve sur le côté du plateau. Si la dernière graine placée se retrouve dans votre réserve, vous bénéficiez d'un tour gratuit.

<div data-demo="Mancala"></div>

## *Flood it!* (`Flooder`)

Définissez le motif de la zone supérieure gauche, qui remplit tous les carrés adjacents de ce motif, en sélectionnant un carré du motif souhaité. Essayez de faire en sorte que la surface entière ai le même motif.

<div data-demo="Flooder"></div>

<!--
## *Blackjack* (`Blackjack`)

Le jeu du [*blackjack*](https://fr.wikipedia.org/wiki/Blackjack_(jeu)).

<div data-demo="Blackjack"></div>

-->

## *Pig game* (`PigGame`)

À chaque tour, un joueur lance plusieurs fois un dé jusqu'à ce qu'il obtienne un 1 ou qu'il décide d'attendre :

- Si le joueur obtient un 1, il ne marque rien et c'est au tour du joueur suivant ;
- Si le joueur obtient un autre chiffre, celui-ci est ajouté au total de son tour et le tour du joueur se poursuit ;
- Si un joueur choisit d'attendre, le total de son tour est ajouté à son score et c'est au tour du joueur suivant de jouer.

Le premier joueur à marquer 100 points ou plus gagne.

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
  <summary>Afficher/masquer</summary>\
  <iframe allow="web-share" id="' + demo + '-code" style="width: 100%;height: 90vh;" src="data:text/html;charset=utf-8,<center><h3>Veuillez patienter…</h3></center>">\
  </iframe>\
  <span>\
    Cliquez <a target="_blank" href="https://faas.q37.info/brython?demo=' + demo + '">ici</a> pour ouvrir cette application dans sa propre page.\
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
