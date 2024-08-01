---
title: "Interface"
menu: "Interface"
weight: 1
---

<!-- À modifier en cas de changement d'URL :
  - 'create' ;
  - 'tutorial' ;
  - 'tutorial/backend' ;
-->

# L'interface

## Introduction

Le codage de l'interface s'appuie sur le langage *HTML*, qui est constitué de balises. Si `balise` est le nom de la balise, la balise ouvrante correspondante se note `<balise>` et la balise fermante, `</balise>`. Entre les deux, on place le contenu de la balise, qui peut être lui-même constitué de balises.

Les balises sont toujours imbriquées, c'est-à-dire que l'on ferme les balises dans l'ordre inverse de leur ouverture. Si les balises ouvrantes sont dans l'ordre `<a>` `<b>` `<c>`, les balises fermantes doivent être dans l'ordre `</c>` `</b>` `</a>`. Tout autre ordre, comme `</a>` `</c>` `</b>` par exemple, est incorrect.

Dans cette page, on pourra directement saisir du code *HTML* et voir en temps réel le résultat s'afficher. À chaque fois que l'on écrira une balise ouvrante, la balise fermante correspondante sera automatiquement ajoutée. De la même manière, l'indentation sera automatique. L'indentation n'est pas strictement nécessaire, mais facilite considérablement la lecture du code.

Certaines balises, pour des raisons historiques, n'ont pas besoin de balise fermante ; elles ne seront donc, de ce fait pas, automatiquement ajoutées.

## L'encadré (`fieldset`)

Commençons par afficher un encadré en utilisant la balise `fieldset` :

<div class="example">
  <div class="todo">
&lt;fieldset&gt;
<br/>
&lt;/fieldset&gt;
  </div>
</div>

Cliquer sur *Afficher/masquer* ci-dessous pour afficher l'éditeur et la prévisualisation et saisir les caractères `<fieldset>` dans l'encadré noir. Comme indiqué ci-dessus, dés que le caractère `>` aura été saisi, l'éditeur rajoutera automatiquement `</fieldset>`. En outre, on verra l'encadré prévu se dessiner dans la zone claire située en-dessous de l'éditeur.

En saisissant un saut de ligne, le curseur ira à la ligne, mais se positionnera également en retrait. C'est l'indentation automatique.

<div data-type="sandbox" data-cursor="1,1">
</div>

Les dimensions de l'encadré affiché dans la zone claire s'ajusteront à son contenu, comme on le verra ci-dessous.

Cliquer à nouveau sur *Afficher/masquer* pour gagner de la place en masquant l'éditeur et la prévisualisation.

## Le champs de saisie (`input`)

Plaçons maintenant un champs de saisie pour l'utilisateur en utilisant la balise `input` (la balise `input` est l'une de ces balises ne nécessitant pas de balise fermante) :

<div class="example">
<div>&lt;fieldset&gt;</div>
<div class="todo">&nbsp;&nbsp;&lt;input&gt;</div>
<div>&lt;/fieldset&gt;</div>
</div>

Saisir dans l'éditeur le code en blanc, celui grisé étant déjà présent.

<div data-type="sandbox" data-cursor="2,3">
<fieldset>
  <!---->
</fieldset>
</div>

On verra un encadré plus petit s'afficher dans l'encadré déjà existant. En cliquant dedans, on verra que l'on peut y saisir du texte ; c'est donc bien une zone de saisie à disposition de l'utilisateur, dont on verra plus tard comment récupérer le contenu.

### Le type de champs de saisie (`type="…"`)

Il existe plusieurs types de champs de saisie, que l'on peut spécifier grâce à l'attribut `type`. Voici comment spécifier un champs de type texte :

<div class="example">
<div>&lt;input <span class="todo">type="text"</span>&gt;</div>
</div>

Par défaut, c'est-à-dire si l'on ne fournit pas l'attribut `type`, les champs de saisie sont de type texte.

À titre d'exemple, voici à quoi ressemble une champs de saisie de type *date* :

<div data-type="sandbox" data-cursor="1,18">
<input type="date"></input>
</div>

En fonction du type de champs, il peut y avoir des aides à la saisie qui apparaissent lorsque l'on clique sur certaines de ses parties.

Voici quelques-unes des autres valeurs possibles pour l'attribut `type` : `checkbox`, `color`, `file`, `radio`, `range`…. On peut remplacer la valeur `date` de l'attribut `type` dans l'éditeur ci-dessus par une de ces valeurs pour en voir les effets.

### Texte d'indication (`placeholder="…"`)

Les champs de saisie de type texte permettent de spécifier un texte qui s'affiche lorsque le champs est vide, cela afin de fournir une indication quant à son contenu. Cela se fait avec l'attribut `placeholder`. Par exemple, voici le code pour indiquer que le champs de saisie texte ci-dessus a pour rôle de recueillir le prénom de l'utilisateur :

<div class="example">
<div>&nbsp;&nbsp;&lt;input <span class="todo">placeholder="Prénom"</span>&gt;</div>
</div>

Voyons le résultat :

<div data-type="sandbox" data-cursor="1,27">
<input placeholder="Prénom"></input>
</div>

On constatera que, dés que l'on commence à saisir du texte dans le champs de saisie, ce texte indicatif disparaît.

### Valeur par défaut (`value="…"`)

Grâce à l'attribut `value`, il est possible de préremplir un champs de saisie de type texte, ce qui peut faciliter le débogage d'une application. 

<div class="example">
<div>&nbsp;&nbsp;&lt;input <span class="todo">value="World"</span>&gt;</div>
</div>

Et le résultat :

<div data-type="sandbox" data-cursor="1,20">
<input value="World">
</div>

Un élément *HTML* peut avoir plusieurs attributs. Leur ordre est sans importance (`<input placeholder="Prénom" value="World">` est équivalent à `<input value="World" placeholder="Prénom">`), mais chacun de ses attributs doit être unique, quelque soit sa valeur.

## Le bouton (`button`)

Ajoutons maintenant un bouton avec la balise `button` :

<div class="example">
<div>&lt;fieldset&gt;</div>
<div>&nbsp;&nbsp;&lt;input placeholder="Prénom" value="World"&gt;</div>
<div class="todo">&nbsp;&nbsp;&lt;button&gt;Envoyer&lt;/button&gt;</div>
<div>&lt;/fieldset&gt;</div>
</div>

Le libellé du bouton (ici *Envoyer*) doit être placé entre la balise ouvrante et fermante.

<div data-type="sandbox" data-cursor="3,3">
<fieldset>
  <input placeholder="Prénom" value="World">
  <!---->
</fieldset>
</div>

## Le séparateur (`hr`)

Ajoutons maintenant une ligne de séparation entre la partie de l'interface servant à la saisie et la partie dédié à l'affichage. Cela va être réalisé grâce à la balise `hr` :

<div class="example">
<div>&lt;fieldset&gt;</div>
<div>&nbsp;&nbsp;&lt;input placeholder="Prénom" value="World"&gt;</div>
<div>&nbsp;&nbsp;&lt;button&gt;Envoyer&lt;/button&gt;</div>
<div class="todo">&nbsp;&nbsp;&lt;hr&gt;</div>
<div>&lt;/fieldset&gt;</div>
</div>

La balise `hr` est également une balise ne nécessitant pas de balise fermante.

<div data-type="sandbox" data-cursor="4,3">
<fieldset>
  <input placeholder="Prénom" value="World">
  <button>Envoyer</button>
  <!---->
</fieldset>
</div>

## La zone d'affichage (`fieldset` & `output`)

On va finir par une zone d'affichage délimitée par un encadré en utilisant la balise `output` imbriquée dans une balise `fieldset` :

<div class="example">
<div>&lt;fieldset&gt;</div>
<div>&nbsp;&nbsp;&lt;input placeholder="Prénom" value="World"&gt;</div>
<div>&nbsp;&nbsp;&lt;button&gt;Envoyer&lt;/button&gt;</div>
<div>&nbsp;&nbsp;&lt;hr&gt;</div>
<div class="todo">&nbsp;&nbsp;&lt;fieldset&gt;</div>
<div class="todo">&nbsp;&nbsp;&nbsp;&nbsp;&lt;output&gt;Zone d'affichage&lt;/output&gt;</div>
<div class="todo">&nbsp;&nbsp;&lt;/fieldset&gt;</div>
<div>&lt;/fieldset&gt;</div>
</div>

Comme la balise `output` est imbriqué dans la balise `fieldset`, son indentation est double.

<div data-type="sandbox" data-cursor="5,3">
<fieldset>
  <input placeholder="Prénom" value="World">
  <button>Envoyer</button>
  <hr>
  <!---->
</fieldset>
</div>

## Bonus (*CSS*)

Le langage *HTML* est dédié à la description de la structure d'une interface par l'indication des éléments qui la compose et leur organisation. Pour contrôler l'apparence de cette interface (couleurs, forme des éléments, polices de caractères, animations…) on utilise un autre langage : *CSS*.

*CSS* n'est pas abordé dans ce tutoriel, mais peut facilement être utilisé dans les applications *Zelbinium*, comme on pourra le constater dans les exemples présents dans la section [*Inspiration*](../../inspiration). Voici cependant un aperçu de ce que l'on peut faire avec *CSS* (le code propre à *CSS* est entre les balises *style*) :

<div data-type="sandbox" data-cursor="6,1">
<div class="big" >
  <div class="little"></div>
</div>
<!---->
<style>
  .big {
    width: 180px;
    height: 180px;
    border-radius: 50%;
    background: conic-gradient(red, orange, yellow, green, blue, violet, red);
    animation: rotation 15s linear infinite;
  }
/**/
  .little {
    width: 50px;
    height: 50px;
    background:
      linear-gradient(45deg, grey 25%, transparent 25%, transparent 75%, grey 75%),
      linear-gradient(-45deg, grey 25%, transparent 25%, transparent 75%, grey 75%);
    background-size: 15px 15px;
    border-radius: 50%;
    position: absolute;
    top: 30%;
    left: 30%;
    animation:
      rotation 2s linear infinite,
      excentricity 5s linear infinite;
  }
/**/
  @keyframes rotation {
    from {
      transform: rotate(0deg) rotateX(360deg);
    }
    to {
      transform: rotate(360deg);
    }
  }
/**/
  @keyframes excentricity {
    from {
      transform: rotate(0deg) translate(50px);
    }
    to {
      transform: rotate(360deg) translate(50px) rotateY(360deg);
    }
  }
  </style>
</div>

## Suite

On va maintenant maintenant passer à la page [*Traitement*](../backend) coder les interactions entre l'utilisateur et l'interface élaborée dans cette page.

<!-- Helpers -->


<link rel="stylesheet" type="text/css" href="/frontend.css"/>
<script src="/frontend.js"></script>

<script>
  buildFrontendSandboxes("Afficher/masquer");
</script>

