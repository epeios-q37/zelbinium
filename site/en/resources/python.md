---
title: "The Python language"
menu: "Python"
weight: 2
---

# The *Python* language

[*Python*](https://en.wikipedia.org/wiki/Python_(programming_language)) is considered one of, if not the most suitable language for beginners. This doesn't mean, however, that it's confined to the educational sector. It's one of the most widely used languages for professional use by people who don't do computers for a living.

For the documentation : <https://docs.python.org/>.

The online demonstrations are based on a slightly modified version of the [*Python* version of the *Atlas* toolkit](https://github.com/epeios-q37/atlas-python). All the methods of the first parameter (usually named *dom*) of the callbacks given to the *launch(…)* function are coroutines so they have to be called with *await*, hence if a function calls one of this method it has to be prefixed with *async* (`async def …`).

Take attention that expressions like:

```python
name = await dom.getValue("Name").strip()
```

are wrong as the *await* is applied to the result of the *strip()* function, and have to be write this way:

```python
name = (await dom.getValue("Name")).strip()
```

so the *strip()* function is applied to the result of the call of the *getValue(…)* coroutine after being completed.