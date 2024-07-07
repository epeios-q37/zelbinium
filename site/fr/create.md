---
title: Créer
menu: Créer
weight: 5
---

<!--
Si URL modifiée, adapter :
- tutorial/backend
-->

# Créer sa propre application

Ici, on va pouvoir créer sa propre application.

Un tutoriel sur la création d'une interface est disponible à la page [*Interface*](../tutorial/frontend) de la section [*Tutoriel*](../tutorial), et un autre sur le codage de la partie traitement à la page [*Traitement*](../tutorial/backend) de la même section *Tutoriel*.


Dans l'encart ci-dessous, on dessinera l'interface de l'application. Une fois celle-ci réalisée, on passera au second encart.


<div id="Frontend" data-cursor="1,1">
<!-- À remplacer par le code HTML de votre interface. -->
</div>

<br/>

Dans l'encart ci-dessous, remplacer le contenu de la constante `BODY` par le contenu élaboré ci-dessus. Ajouter les fonctionnalités désirées et cliquer sur *Run* pour lancer l'application.

<pre id="Backend" data-cursor="4,1">
import atlastk

BODY = """
&lt;center>
&lt;h5>À remplacer par le code HTML correspondant à votre interface.&lt;/h5>
&lt;/center>
"""

async def acConnect(dom):
  await dom.inner("", BODY)

CALLBACKS = {
  "": acConnect,
}

atlastk.launch(CALLBACKS)
</pre>



<!-- helpers -->


<link rel="stylesheet" type="text/css" href="/frontend.css"/>
<script src="/frontend.js"></script>

<link rel="stylesheet" type="text/css" href="/backend.css"/>
<script src="/backend.js"></script>

<script>
  buildFrontendSandbox(document.getElementById("Frontend"), "Afficher/masquer l'interface");

  appendBrythonInNewTabCode();

  buildBackendSandbox(document.getElementById("Backend"), "Afficher/masquer l'application", "Ouvrir dans un nouvel onglet");
</script>
