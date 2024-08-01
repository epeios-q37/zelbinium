---
title: "Traitement"
menu: "Traitement"
weight: 2
---

<!--
À modifier en cas de changement d'URL :
  - 'create' ;
  - 'tutorial' ;
  - 'tutorial/frontend' ;
-->

# Le traitement

## Introduction

L'interface ayant été créée à la [page dédiée à l'interface](../frontend), on peut passer au codage de la partie traitement de l'application.

L'application pourra être lancée, directement de cette page, à chaque étape de son élaboration pour une meilleur compréhension de la finalité du code introduit lors de chaque étape.

## Affichage de l'interface

### Description de l'interface (`BODY`)

Créons une constante avec le contenu qui a été élaboré à la page [*Interface*](../frontend). Par convention, avec *Python* (et beaucoup d'autres langages), le nom d'une constante est uniquement constitué de lettres majuscules non accentuées, de chiffres et du caractère `_`.

Le nom de la constante ici est `BODY`, et elle est définie de la manière suivante :

<div class="example">
<pre>
<span class="todo">BODY = """</span>
&lt;fieldset>
  &lt;input placeholder="Prénom" value="World">
  &lt;button>Envoyer&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Zone d'affichage&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
<span class="todo">"""</span>
</pre>
</div>

La séquence de caractères `"""` est un délimiteur caractérisant une chaîne de caractères qui s'étend sur plusieurs lignes. En *Python*, on peut également utiliser les caractères `'` ou `"` pour délimiter une chaîne de caractères, mais, dans ce cas, la chaîne de caractère ne peut pas contenir de sauts de ligne.

### Fonction d'affichage de l'interface (`acConnect`)

Écrivons maintenant la fonction qui va effectuer le rendu (affichage de la représentation visuelle) du contenu de la constante `BODY` que l'on vient de créer. 

Pour cela, on va utiliser un module appelé *atlastk*, un module étant une sorte de boîte à outils offrant tout un ensemble de fonctionnalités.

Il faut, en premier lieu, déclarer à l'environnement d'exécution que l'on veut utiliser ce module. Ceci est réalisé grâce au mot-clef `import`. Cette déclaration doit être faite avant la première utilisation d'une des fonctionnalités du module concerné, ce qui fait qu'elle est souvent placée vers le début.

<div class="example">
<pre>
<div class="todo">import atlastk</div>
BODY = """
&lt;fieldset>
  &lt;input placeholder="Prénom" value="World">
  &lt;button>Envoyer&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Zone d'affichage&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""
</pre>
</div>

Écrivons maintenant la fonction qui va procéder au rendu proprement dit. Par convention, on va appeler cette fonction `acConnect`, `ac`, car associée à une action, et `Connect`, car exécutée lors d'une nouvelle connexion.

Voilà à quoi elle ressemble :

<div class="example">
<pre class="todo">
async def acConnect(dom):
  await dom.inner("", BODY)
</pre>
</div>

La définition (2<sup>de</sup> ligne) de la fonction `acConnect` est placé en retrait de sa déclaration (1<sup>re</sup> ligne) ; on dit qu'elle est « indentée ». Généralement, cette indentation n'est pas obligatoire est n'est mise en œuvre que pour faciliter la lecture du code, mais, en *Python*, cette indentation fait partie de la syntaxe du langage, et son absence provoquera des erreurs.

`dom` est un paramètre que reçoit la fonction `acConnect`. C'est un objet fourni par le module *atlastk*. En raison d'impératifs techniques, la plupart des fonctions appartenant à cet objet doivent être appelées avec le mot-clef `await`. En outre, toute fonction qui contient au moins une fonction `await` doit être déclarée avec le mot-clef `async`.

L'utilisation des mots-clefs `async` et `await` est uniquement dû à la technologie permettant d'exécuter des applications *Python* dans un navigateur web. Ils sont rarement utilisés dans un programme *Python* exécuté dans un environnement d'exécution traditionnel, mais sont indispensables dans ce contexte ; leur oubli ne provoquera pas d'erreur, mais empêchera les applications de fonctionner correctement.

La méthode `inner` de l'objet `dom` (une méthode est une fonction rattachée à un objet) permet de remplacer le contenu d'un élément de l'interface graphique.

Ici, l'élément est identifié par une chaîne vide (`""`). Cet identifiant est spécial et désigne l'interface dans sa globalité. La totalité de l'interface graphique va ainsi être constituée du contenu de la constante `BODY` précédemment définie.

Comme la fonction `acConnect` fait appel au module *atlastk*, mais utilise également le contenu de la constante `BODY`, elle sera placée de la manière suivante :

<div class="example">
<pre>
import atlastk
<span></span>
BODY = """
&lt;fieldset>
  &lt;input placeholder="Prénom" value="World">
  &lt;button>Envoyer&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Zone d'affichage&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""
<div class="todo">
async def acConnect(dom):
  await dom.inner("", BODY)
</div></pre>
</div>

### Association fonction d'affichage / nouvelle connexion (`CALLBACKS`)

On va maintenant associer cette fonction à une action, en l'occurrence celle correspondant à une nouvelle connexion. Pour cela, on va définir une constante nommée `CALLBACKS`, qui va ressembler à ceci :

<div class="example">
<pre class="todo">
CALLBACKS = {
  "": acConnect,
}
</pre>
</div>

`CALLBACKS` est ce qu'on appelle un dictionnaire, grâce auquel on va pouvoir associer une action identifiée par la chaîne vide (`""`) à la fonction `acConnect` précédemment définie. La chaîne vide, dans ce contexte, identifie l'action associée à une nouvelle connexion.

Appelons maintenant la fonction qui va traiter tout cela :

<div class="example">
<pre class="todo">
atlastk.launch(CALLBACKS);
</pre>
</div>

`atlastk` fait référence au module du même nom importé précédemment et `launch` est une de ses fonctions à laquelle on passe, en l’occurrence, la constante `CALLBACKS` précédemment définie. C'est cette fonction qui va lancer le rendu de l'interface et prendre en charge les interactions de l'utilisateur avec l'interface tel que définies dans la `CALLBACKS`

Ci-dessous, on trouvera l'ensemble du code élaboré jusqu'à présent :

<pre data-type="sandbox">
import atlastk

BODY = """
&lt;fieldset>
  &lt;input placeholder="Prénom" value="World">
  &lt;button>Envoyer&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Zone d'affichage&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""

async def acConnect(dom):
  await dom.inner("", BODY)

CALLBACKS = {
  "": acConnect,
}

atlastk.launch(CALLBACKS)
</pre>

En cliquant sur *Run*, cela entraînera l'affichage de l'interface telle qu'élaborée à la page [*Interface*](../frontend). Cependant, cliquer sur le bouton *Envoyer* sera sans effet, car il manque la partie du code qui prend en charge cette action. C'est ce code que l'on va élaborer maintenant.

## Prise en charge du bouton *Envoyer*

### Association clic sur bouton *Envoyer* / action (`xdh:onevent="Submit"`)

Modifions le code de l'application pour indiquer quelle action associer au fait de cliquer sur le bouton *Envoyer*. Pour cela, on va mettre à jour le code *HTML* :

<div class="example">
<pre>
BODY = """
&lt;fieldset>
  &lt;input placeholder="Prénom" value="World">
  &lt;button <span class="todo">xdh:onevent="Submit"</span>>Envoyer&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Zone d'affichage&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""
</div>

Par ce code (`xdh:onevent="Submit"`), on ajoute un attribut à l'élément *HTML* `button`. Pour chaque élément *HTML*, comme on l'a vu à la page [*Interface*](../frontend), on peut mettre en œuvre une série d'attributs prédéfinis. Mais on peut aussi *étendre* *HTML* et créer ses propres attributs (et ses propres éléments aussi). Ces extensions du code *HTML* doivent être mis en œuvre dans un espace de nom. Ici, l'espace de nom est `xdh` est le `:` signifie que l'identifiant qui suit (`onevent`) appartient à cet espace de nom.

En analysant ce code, le navigateur web, qui est chargé du rendu du code *HTML*, ignorera tout ce qui appartient a un espace de nom qu'il ne connaît pas. C'est le module *atlastk* qui, en analysant à son tour le code *HTML*, détectera la présence des composants associés à l'espace de nom `xdh` et en assurera la prise en charge.

Ici, l'attribut est `xdh:onevent` et sa valeur `Submit`. Cela signifie qu'à l'action par défaut du bouton concerné (le fait de cliquer dessus) est associé un événement de nom `Submit`.

Voyons maintenant le code dans sa globalité :

<pre data-type="sandbox">
import atlastk

BODY = """
&lt;fieldset>
  &lt;input placeholder="Prénom" value="World">
  &lt;button xdh:onevent="Submit">Envoyer&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Zone d'affichage&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""

async def acConnect(dom):
  await dom.inner("", BODY)

CALLBACKS = {
  "": acConnect,
}

atlastk.launch(CALLBACKS)
</pre>

L'application affiche maintenant l'interface comme précédemment, mais cette fois-ci, un clic sur le bouton *Envoyer* provoque l'affichage d'un message d'erreur. Celui-ci signale qu'une action *Submit* bien été associée au clic sur le bouton *Envoyer*, mais qu'il n'y a aucun code associé à cette action.

Remédions à cela.

### Fonction associée au bouton *Envoyer* (`acSubmit`)

À des fins didactiques, le fait de cliquer sur le bouton va, dans un premier temps, simplement afficher un message signalant que le clic a bien été pris en compte.

Voici à quoi va ressembler ce code :

<div class="example">
<pre class="todo">
async def acSubmit(dom):
  await dom.alert('Clic sur le bouton "Envoyer" détecté !')
</pre>
</div>

On retrouve les différents éléments (`async`, `await`, paramètre `dom`…) que l'on a découvert avec la fonction `acConnect`. La méthode `alert` de l'objet correspondant au paramètre `dom` affiche une boite de dialogue contenant la chaîne passée en paramètre.

### Association fonction `acSubmit` / action `Submit` (`CALLBACKS`)

On va maintenant associer cette fonction à l'action `Submit` en modifiant la constante `CALLBACKS` de la façon suivante :

<div class="example">
<pre>
CALLBACKS = {
  "": acConnect,
<span class="todo">  "Submit": acSubmit,</span>
}
</pre>
</div>

Voici le code dans son ensemble :

<pre data-type="sandbox">
import atlastk

BODY = """
&lt;fieldset>
  &lt;input placeholder="Prénom" value="World">
  &lt;button xdh:onevent="Submit">Envoyer&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Zone d'affichage&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""

async def acConnect(dom):
  await dom.inner("", BODY)

async def acSubmit(dom):
  await dom.alert('Clic sur le bouton "Envoyer" détecté !')

CALLBACKS = {
  "": acConnect,
  "Submit": acSubmit,
}

atlastk.launch(CALLBACKS)
</pre>

Cette fois-ci, un clic sur le bouton *Envoyer* affiche le message attendu (*Clic sur le bouton "Envoyer" détecté !*).

Finalisons maintenant la fonction `acSubmit`.

## Récupération d'une donnée utilisateur

### Identification champs de saisie pour récupération contenu (`id="Input"`)

Modifions le code *HTML* afin d'ajouter un identifiant au champs de saisie et ainsi pouvoir récupérer son contenu :

<div class="example">
<pre>
BODY = """
&lt;fieldset>
  &lt;input placeholder="Prénom" value="World" <span class="todo">id="Input"</span>>
  &lt;button xdh:onevent="Submit">Envoyer&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Zone d'affichage&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""
</div>

L'attribut `id` permet d'assigner un identifiant à un élément *HTML* pour pouvoir s'y référer, comme on le verra par la suite. Cet identifiant doit bien entendu être unique parmi l'ensemble des éléments constituant un document *HTML*.

### Récupération du contenu d'un élément *HTML* (`dom.getValue(…)`)

Modifions la fonction `acSubmit` pour récupérer le contenu du champs de saisie et l'afficher dans la boite de dialogue :

<div class="example">
<pre>
async def acSubmit(dom):
<span class="todo">  input = await dom.getValue("Input")</span>
<span class="old">  await dom.alert('Clic sur le bouton "Envoyer" détecté !')</span>
<span class="todo">  await dom.alert(f'Valeur champs de saisie : "{input}"')</span>
</pre>
</div>

La méthode `getValue(…)` permet de récupérer la valeur d'un élément *HTML*, en l’occurrence celui d'identifiant `Input` correspondant au champs de saisie. Le code `input = …` permet d'affecter cette valeur à la variable d'identifiant `input`.

La chaîne de caractères donnée comme paramètre à la méthode `alert(…)`, du fait d'être précédée par le caractère `f`, est une  *f-string* et subit, de ce fait, un traitement particulier. En effet, toute expression entre accolades (`{}`) présente dans un *f-string* est évaluée. Dans notre cas, la chaîne de caractères contient l'expression `{input}`. Cette expression sera remplacée par le contenu de la variable `input` lors de l'exécution de l'application c'est-à-dire, comme indiqué précédemment, par le contenu du champs de saisie.

Testons le code avec l'ensemble des modifications :

<pre data-type="sandbox">
import atlastk

BODY = """
&lt;fieldset>
  &lt;input placeholder="Prénom" value="World" id="Input">
  &lt;button xdh:onevent="Submit">Envoyer&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Zone d'affichage&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""

async def acConnect(dom):
  await dom.inner("", BODY)

async def acSubmit(dom):
  input = await dom.getValue("Input");
  await dom.alert(f'Valeur champs de saisie : "{input}"')

CALLBACKS = {
  "": acConnect,
  "Submit": acSubmit,
}

atlastk.launch(CALLBACKS)
</pre>

En cliquant sur le bouton *Envoyer*, la boite de dialogue affiche bien la valeur récupérée dans le champs de saisie (*World*).

## Affichage de contenu dans l'interface

### Identification zone d'affichage (`id="Output"`)

Comme pour le champs de saisie, on va affecter à l'élément correspondant à la zone d'affichage un identifiant qui lui sera propre (`Output`) :

<div class="example">
<pre>
BODY = """
&lt;fieldset>
  &lt;input placeholder="Prénom" value="World" id="Input">
  &lt;button xdh:onevent="Submit">Envoyer&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output <span class="todo">id="Output"</span>>Zone d'affichage&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""
</pre>
</div>

### Modification du contenu d'un élément *HTML* (`dom.setValue(…)`)

Altérons la fonction `acSubmit` pour modifier le contenu de la zone d'affichage afin d'afficher un texte contenant la donnée saisie par l'utilisateur, celle-là même qui est stockée dans la variable `input` :

<div class="example">
<pre>
async def acSubmit(dom):
  input = await dom.getValue("Input")
<span class="old">  await dom.alert(f'Valeur champs de saisie : "{input}"')</span>
<span class="todo">  await dom.setValue("Output", f'Bonjour, {input} !')</span>
</pre>
</div>

La méthode `setValue(…)` permet de modifier la valeur d'un élément *HTML*, en l’occurrence celui d'identifiant `Output`, avec la chaîne de caractères passée en paramètre.

Testons le code avec l'ensemble des modifications :

<pre data-type="sandbox">
import atlastk

BODY = """
&lt;fieldset>
  &lt;input placeholder="Prénom" value="World" id="Input">
  &lt;button xdh:onevent="Submit">Envoyer&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output id="Output">Zone d'affichage&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""

async def acConnect(dom):
  await dom.inner("", BODY)

async def acSubmit(dom):
  input = await dom.getValue("Input");
  await dom.setValue("Output", f'Bonjour, {input} !')

CALLBACKS = {
  "": acConnect,
  "Submit": acSubmit,
}

atlastk.launch(CALLBACKS)
</pre>

En cliquant sur le bouton *Envoyer*, il y a bien un message de salutation reprenant le texte contenu dans le champs de saisie qui s'affiche. On peut réaliser quelques essais supplémentaires en changeant le contenu de ce champs de saisie.

## Amélioration de l'ergonomie

### Focus sur un élément *HTML* (`dom.focus(…)`)

On peut remarquer qu'après avoir cliqué sur le bouton *Envoyer*, il est nécessaire de cliquer sur le champs de saisie pour pouvoir effectuer une nouvelle saisie. On dit que le champs de saisie « perd le focus ». Sur un smartphone, on remarque d'ailleurs que le fait d'appuyer sur le bouton *Envoyer* ferme le clavier virtuel.

On dit d'un élément qu'il a le focus lorsque c'est cet élément qui est la cible des actions de l'utilisateur. Ainsi, lorsque le champs de saisie a le focus, c'est dans ce champs qu'apparaissent les caractères saisis au clavier.

Modifions le code pour que le champs de saisie retrouve le focus à chaque fois que l'on valide la saisie, ainsi qu'à l'ouverture d'une session. Pour cela, modifions les fonctions `acConnect` et `acSubmit` :

<div class ="example">
<pre>
async def acConnect(dom):
  await dom.inner("", BODY)
  <span class="todo">await dom.focus("Input")</span>
</pre>
<pre>
async def acSubmit(dom):
  input = await dom.getValue("Input");
  await dom.setValue("Output", f'Bonjour, {input} !')
  <span class="todo">await dom.focus("Input")</span>
</pre>
</div>

La méthode `focus(…)` permet de donner le focus à l'élément dont l'identifiant et passé en paramètre. On notera qu'un seul élément (ou aucun) peut avoir le focus à un moment donné.

Testons le résultat :

<pre data-type="sandbox">
import atlastk

BODY = """
&lt;fieldset>
  &lt;input placeholder="Prénom" value="World" id="Input">
  &lt;button xdh:onevent="Submit">Envoyer&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output id="Output">Zone d'affichage&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""

async def acConnect(dom):
  await dom.inner("", BODY)
  await dom.focus("Input")

async def acSubmit(dom):
  input = await dom.getValue("Input");
  await dom.setValue("Output", f'Bonjour, {input} !')
  await dom.focus("Input")

CALLBACKS = {
  "": acConnect,
  "Submit": acSubmit,
}

atlastk.launch(CALLBACKS)
</pre>

Au lancement, on verra le curseur clignoter dans le champs de saisie, signe qu'elle possède le focus. Sur *Android* ou *iOs*, selon le navigateur employé, il demeure nécessaire de cliquer sur le champs de saisie pour pouvoir saisir du texte (affichage du clavier virtuel) mais, après avoir cliqué sur *Envoyer*, le clavier virtuel reste ouvert et l'on pourra saisir du texte sans avoir à cliquer auparavant sur le champs de saisie.

### Bonus

On va encore réaliser deux petites modifications en employant certains des élément déjà utilisés. La première dans le code *HTML*,  pour pouvoir valider la donnée saisie directement avec la touche *Entrée* d'un clavier physique ou virtuel, la seconde dans le code de la fonction `acSubmit`, pour vider le champs de saisie après chaque validation afin de faire place nette pour une nouvelle saisie.

Voici en quoi consistent ces modifications :

<div class="example">
<pre>
BODY = """
&lt;fieldset>
  &lt;input id="Input" <span class="todo">xdh:onevent="Submit" </span>placeholder="Prénom" value="World">
  &lt;button xdh:onevent="Submit">Envoyer&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Zone d'affichage&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""
<span></span>
…
<span></span>
async def acSubmit(dom):
  input = await dom.getValue("Input");
  await dom.setValue("Output", f'Bonjour, {input} !')
  await dom.focus("Input")
  <span class="todo">await dom.setValue("Input", "")</span>
</pre>
</div>

Voyons ce que ça donne :

<pre data-type="sandbox">
import atlastk

BODY = """
&lt;fieldset>
  &lt;input id="Input" xdh:onevent="Submit" placeholder="Prénom" value="World">
  &lt;button xdh:onevent="Submit">Envoyer&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output id="Output">Zone d'affichage&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""

async def acConnect(dom):
  await dom.inner("", BODY)
  await dom.focus("Input")

async def acSubmit(dom):
  input = await dom.getValue("Input");
  await dom.setValue("Output", f'Bonjour, {input} !')
  await dom.focus("Input")
  await dom.setValue("Input", "")

CALLBACKS = {
  "": acConnect,
  "Submit": acSubmit,
}

atlastk.launch(CALLBACKS)
</pre>

On constatera que, dorénavant, on peut utiliser la touche *Entrée* du clavier physique ou virtuel pour valider la saisie, et que le champs de saisie se vide après chaque validation.

## Poursuivre

La section [*Inspiration*](../../inspiration) propose tout un ensemble d'applications permettant de découvrir de nouvelles fonctionnalités, applications que l'on peut lancer et dont on peut modifier le code source *in situ* pour en explorer le fonctionnement.  
La section [*Créer*](../../create), elle, est dédiée à la création de ses propres applications.

<!-- Helpers -->

<link rel="stylesheet" type="text/css" href="/backend.css"/>
<script src="/backend.js"></script>

<script>
  buildBackendSandboxes("Afficher/masquer", "Ouvrir dans un nouvel onglet")
</script>

