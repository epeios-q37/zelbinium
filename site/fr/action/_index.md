---
title: Action !
menu: Action !
weight: 2
bookCollapseSection: false
---

<!--
Si URL modifiée, modifier :
- modifier (ancres sur les différentes section du partage d'application)
  - 3fqr9w7s,
  - jjhz4c94,
  - c49crxbw ;
-->

# *Action !*

Dans cette section du site, on verra comment réaliser différentes actions relatives à une application et son code source directement à partir d'un navigateur web. Le point de départ sera un encart comme celui-ci :

<details>
  <summary style="cursor; pointer; outline-style: none;">Afficher/masquer</summary>
  <iframe allow="web-share" style="width: 100%; height: 80vh;" src="https://faas.q37.info/brython?demo=Messages">
  </iframe>
</details>

L'application utilisée à titre d’exemple dans cette section permet d"échanger des messages avec n'importe qui juste en lui faisant scanner un [code QR](https://fr.wikipedia.org/wiki/Code_QR) ou en lui envoyant un lien généré par l'application avec son smartphone (plus de détails seront donnés ci-dessous).

<div style="width: 100%; text-align: center">
  <img style="margin: auto;" src="./Action.png"></img>
  <div style="font-size: small;">
    <span>Crée avec </span>
    <a href="https://framalab.org/gknd-creator/" target="_blank">
      <em>GéGé</em></a><span>.</span>
  </div>
</div>


Dans les sections suivantes, on sera invité à réaliser différentes actions sur l'encart en début de page. 

## Lancer une application

Pour lancer l'application, il suffit de cliquer sur le bouton *Run*. Cela va masquer l'éditeur du code source puis, au bout d'un temps variable dépendant de la complexité de l'application, l'interface de celle-ci va s'afficher. Cliquer sur *Code* masquera/affichera le code source de l'application.

<details>
  <summary style="cursor; pointer; outline-style: none;">Afficher/masquer</summary>
  <iframe allow="web-share" style="width: 100%; height: 80vh;" src="https://faas.q37.info/brython?demo=Messages">
  </iframe>
</details>

## Partager l’accès à une application
<!--
Voir commentaire en tête de fichier si titre modifié.
-->

### Avec un code QR
<!--
Voir commentaire en tête de fichier si titre modifié.
-->

Voyons comment partager l’accès à une application pour que plusieurs personnes puissent l'utiliser en même temps, chacun avec son propre appareil (smartphone, tablette, ordinateur personnel…).

Dans l'encart ci-dessous, le bouton *Run* pour lancera l'application qui s'affichera au bout d'un petit moment.

<details>
  <summary style="cursor; pointer; outline-style: none;">Afficher/masquer</summary>
  <iframe allow="web-share" style="width: 100%; height: 80vh;" src="https://faas.q37.info/brython?demo=Messages">
  </iframe>
</details>

Tout en bas, les icônes suivantes vont s'afficher :

![Zone à cliquer pour afficher le code QR](./FooterQRCode.png)

En cliquant sur l'icône pointée par la flèche, voici ce qui va s'afficher :

![Code QR](./FooterQRCodeOpen.png)

On aperçoit ici un [code QR](https://fr.wikipedia.org/wiki/Code_QR), pointé par la flèche. En cliquant dessus, un autre onglet va s'ouvrir qui donnera également accès à l'application. En passant d'un onglet à l'autre, on s'apercevra que les messages écrits dans un onglet seront également affichés dans l'autre onglet. Il est possible d'ouvrir simultanément plus de deux onglets.

Pour pouvoir converser avec quelqu'un à proximité, il suffit de lui faire scanner le code QR avec son appareil (smartphone, tablette…). Cela lui donnera accès à l'application. Vous pourrez ainsi échanger des messages, chacun avec son appareil.

### Avec un lien
<!--
Voir commentaire en tête de fichier si titre modifié.
-->

Pour échanger des messages avec une personne qui ne peut pas scanner le code QR, soit parce qu'elle n'est pas à proximité, soit parce que ce n'est pas possible ou trop compliqué avec son appareil, il est quand même possible de lui donner accès à l'application.

![](./FooterShare.png)

Pour ce faire, il suffit de cliquer sur l'icône pointée par la flèche. S'offrira alors la possibilité de partager l’accès à l'application d'une manière similaire au partage d'une vidéo, d'une photo, d'un lien…

Il est possible que certains appareils, ou certains navigateurs, n'offrent pas cette possibilité de partage. S'affichera alors ceci : 

![](./FooterCopy.png)

En cliquant sur l'icône signalée par la flèche, un lien est alors copié dans le presse-papier, facilitant son envoi, par e-mail par exemple ou n'importe quelle autre application de messagerie. En ouvrant ce lien dans son navigateur web, ce qui devrait se faire automatiquement en cliquant sur le lien, le destinataire du message pourra accéder à l'application comme s'il avait scanné le code QR.

Sur les dispositifs mobiles, il est également possible d'appuyer de manière prolongée sur le code QR pour faire apparaître un menu offrant la possibilité de partager le lien de l'application.

Toutes les fonctionnalités de partage présentées sur cette page sont automatiquement disponibles pour toutes les applications *Zelbinium*, qu'il s'agisse de celles proposées sur ce site, ou de celles créées de toutes pièces.

## Explorer le code source d'une application

Le [code source](https://fr.wikipedia.org/wiki/Code_source) d'une application est la liste des instructions constituant cette application. Ce code source peut être découpé en plusieurs fichiers.

Pour faciliter leur manipulation, toutes les applications présentes sur ce site tiennent en un seul fichier. Il suffit de cliquer dans l'éditeur (après avoir cliquer sur *Code* si ce dernier est masqué) pour pouvoir se déplacer dans le code source et ainsi l'explorer.

<details>
  <summary style="cursor; pointer; outline-style: none;">Afficher/masquer</summary>
  <iframe allow="web-share" style="width: 100%; height: 80vh;" src="https://faas.q37.info/brython?demo=Messages">
  </iframe>
</details> 


## Modifier le code source d'une application

Modifier le code source d'une application est possible directement dans l'éditeur. En cliquant sur *Run*, ce sera la version modifiée de l'application qui sera exécutée.

<details>
  <summary style="cursor; pointer; outline-style: none;">Afficher/masquer</summary>
  <iframe allow="web-share" style="width: 100%; height: 80vh;" src="https://faas.q37.info/brython?demo=Messages">
  </iframe>
</details> 

<!--
## Créer sa propre application
-->

Pour aller plus loin, la section [*Inspiration*](../inspiration/) comporte d'autres applications à explorer et modifier à loisir…

<!-- Helpers -->


<link rel="stylesheet" type="text/css" href="/action.css"/>
<script src="/action.js"></script>

<script>
  actionMain();
</script>

