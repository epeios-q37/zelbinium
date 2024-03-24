---
title: "The Atlas toolkit"
menu: "Atlas toolkit"
weight: 8
---

# The *Atlas* toolkit

The *Atlas* toolkit (https://atlastk.org/) is a software library that makes it easy to add a graphical interface to an application and bring it online. This library is at the heart of *Zelbinium*.

Documentation on its [API](https://en.wikipedia.org/wiki/API) can be found at <https://atlastk.org/api>.

There are a number of modules based on this library.

The [*term2web*](https://pypi.org/project/term2web/) module, by writing a single line (`from term2web import *`) at the beginning of the source file, displays a *Python* program based on a user interface in a web browser. You can also style the output using *CSS*. Most programs for beginners are based on a text interface, therefor using *term2web* makes these programs more appealing.

The [*tortoise*](https://pypi.org/project/tortoise/) module is an implementation of the [*Logo* turtle](https://en.wikipedia.org/wiki/Logo_(programming_language)). The difference with the [turtle](https://docs.python.org/3/library/turtle.html) module supplied with *Python* is that the resulting graphics are displayed in a web browser and can be shared on the Internet. Here's an example of a graph generated with this module:

![](https://s.q37.info/34xmsbfb.png)


The [*EduTK*](https://pypi.org/project/edutk/) module can be used to create exercises for learning to program. These exercises, thanks to the *toolkit* *Atlas*, are executed in a graphical environment without the need for direct GUI programming.

Here's what a typical programming exercise looks like:

![](https://s.q37.info/p3g3svdw.png)

Same exercise with the *EduTK* module:

![](https://s.q37.info/3tmm4gmh.png)