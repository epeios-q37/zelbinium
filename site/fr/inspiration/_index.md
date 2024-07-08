---
title: "Inspiration"
menu: "Inspiration"
weight: 4
bookCollapseSection: false
---

<!--
Si URL modifiée, adapter :
- tutorial/backend
-->

# Inspiration

Voici quelques applications dont certaines permettent aux utilisateurs d'interagir entre eux (prévisualisation avec deux panneaux).  L'ensemble de ces applications sont regroupées dans le dépôt à l'adresse <https://github.com/epeios-q37/zelbinium>. Le terme entre parenthèses est le nom du dossier dans lequel se situe le code source de chaque application.

En cliquant *Afficher/masquer* sous l'aperçu d'une application, vous aurez accès à son encart à partir duquel l'application pourra être lancée, partagée, explorée, modifiée <!--et servir d'inspiration pour créer ses propres applications!--> comme détaillé dans la section [*Action !*](../action/).

## *Hello world* (`Hello`)

Programme de type [*Hello world*](https://fr.wikipedia.org/wiki/Hello_world) montrant les bases d'une application *Zelbinium*. L'application affiche simplement une salutation reprenant le contenu d'un champ texte.

<div data-demo="Hello"></div>

## *Hello world* partagé (`Hellos`)

Même application que précédemment, mais les salutations sont affichées à tous les utilisateurs connectés à l'application. Montre les bases d'une application permettant à ses utilisateurs d'interagir.

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

<!--
Prenez les graines dans un emplacement de votre côté et placez-en une dans chaque emplacement suivant, dans le sens inverse des aiguilles d'une montre et en sautant la réserve de votre adversaire. Si votre dernière graine atterrit dans un emplacement vide, déplacez les graines de l'emplacement opposé dans votre réserve. Le but est d'obtenir le plus grand nombre de graines dans votre réserve sur le côté du plateau. Si la dernière graine placée se retrouve dans votre réserve, vous bénéficiez d'un tour gratuit.
-->

<div data-demo="Mancala"></div>

## *Flood it!* (`Flooder`)

Le célèbre jeu de stratégie.

<!--
Définissez le motif de la zone supérieure gauche, qui remplit tous les carrés adjacents de ce motif, en sélectionnant un carré du motif souhaité. Essayez de faire en sorte que la surface entière ai le même motif.
-->

<div data-demo="Flooder"></div>

<!--
## *Blackjack* (`Blackjack`)

Le jeu du [*blackjack*](https://fr.wikipedia.org/wiki/Blackjack_(jeu)).

<div data-demo="Blackjack"></div>

-->

## *Pig game* (`PigGame`, avec son)

Le célèbre jeu de dés.

**Attention : ce jeu comporte des effets sonores !**

<!--
À chaque tour, un joueur lance plusieurs fois un dé jusqu'à ce qu'il obtienne un 1 ou qu'il décide d'attendre :

- Si le joueur obtient un 1, il ne marque rien et c'est au tour du joueur suivant ;
- Si le joueur obtient un autre chiffre, celui-ci est ajouté au total de son tour et le tour du joueur se poursuit ;
- Si un joueur choisit d'attendre, le total de son tour est ajouté à son score et c'est au tour du joueur suivant de jouer.

Le premier joueur à marquer 100 points ou plus gagne.

-->

<div data-demo="PigGame"></div>

<!-- Helpers -->


<link rel="stylesheet" type="text/css" href="/inspiration.css"/>
<script src="/inspiration.js"></script>

<script>
  demosFill("Afficher/masquer", "Veuillez patienter…", "Ouvrir dans un nouvel onglet");
</script>
