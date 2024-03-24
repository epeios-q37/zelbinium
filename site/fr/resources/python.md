---
title: "Le langage Python"
menu: "Python"
weight: 2
---

# Le langage *Python*

Bien que considéré comme l'un des meilleur langages, si ce n'est le meilleur, pour débuter la programmation, [*Python*](https://fr.wikipedia.org/wiki/Python_(langage)) n'est pas pour autant cantonné au domaine éducatif. C'est l'un des langages les plus utilisés professionnellement par des gens dont l'informatique n'est pas le métier.

La documentation en français : <https://docs.python.org/fr/>.

Les démonstrations en ligne s'appuient sur une version légèrement modifiée de la [version *Python* du *toolkit* *Atlas*](https://github.com/epeios-q37/atlas-python). Toutes les méthodes du premier paramètre (habituellement nommé *dom*) des *callbacks* passés à la fonction *launch(…)* sont des coroutines qui nécessitent d'être appelés avec le mot-clef *await*, et par conséquent les fonctions appelant une des ces méthodes nécessitent d'être préfixées avec le mot-clef *async* (`async def …`).

Notez que les expressions comme :

```python
name = await dom.getValue("Name").strip()
```

sont incorrectes du fait que le *await* est appliqué au résultat de la fonction *strip()*, et doivent donc être articulées de la manière suivante :

```python
name = (await dom.getValue("Name")).strip()
```

de façon à ce que la fonction *strip()* soit appliquée à la valeur retournée par la *coroutine* *getValue(…)* une fois son exécution achevée.