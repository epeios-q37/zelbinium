---
title: "Processing"
menu: "Processing"
weight: 2
---

<!--
À modifier en cas de changement d'URL :
  - 'create' ;
  - 'tutorial' ;
  - 'tutorial/frontend' ;
-->

# The processing

## Introduction

Now that the interface has been created on the [page dedicated to the interface](../frontend), we can move on to coding the processing part of the application.

The application can be launched directly from this page at each stage of its development, for a better understanding of the purpose of the code introduced at each stage.

## Interface displaying

### Interface description (`BODY`)

Let's create a constant with the content that has been elaborated on the [*Interface*](../frontend) page. By convention, with *Python* (and many other languages), the name of a constant consists only of uppercase letters, numbers and the `_` character.

The name of the constant here is `BODY`, and it is defined as follows:

<div class="example">
<pre>
<span class="todo">BODY = """</span>
&lt;fieldset>
  &lt;input placeholder="Name" value="World">
  &lt;button>Send&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Display area&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
<span class="todo">"""</span>
</div>

The `“”"` character sequence is a delimiter characterizing a string that spans several lines. In *Python*, you can also use the characters `'` or `"` to delimit a string, but, in this case, the string cannot contain line breaks.

### Interface display function (`acConnect`)

Let's now write the function that will render (display the visual representation of) the contents of the `BODY` constant we've just created. 

To do this, we'll use a module called *atlastk*, a module being a kind of toolbox offering a full range of functions.

The first step is to declare to the runtime environment that we want to use this module. This is done using the `import` keyword. This declaration must be made before the first use of one of the module's functionalities, so it is often placed near the beginning.

<div class="example">
<pre>
<div class="todo">import atlastk</div>
BODY = """
&lt;fieldset>
  &lt;input placeholder="Name" value="World">
  &lt;button>Send&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Display area&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""
</pre>
</div>

Now let's write the function that will actually perform the rendering. By convention, we'll call this function `acConnect`, `ac`, because it's associated with an action, and `Connect`, because it's executed when a new connection is made.

Here's what it looks like:

<div class="example">
<pre class="todo">
async def acConnect(dom):
  await dom.inner("", BODY)
</pre>
</div>

The definition (2<sup>nd</sup> line) of the `acConnect` function is set back from its declaration (1<sup>rst</sup> line); it is said to be “indented”. Generally, this indentation is not mandatory and is only used to make the code easier to read, but in *Python*, the indentation is part of the language's syntax, and its absence will cause errors.

`dom` is a parameter received by the `acConnect` function. It is an object provided by the *atlastk* module. For technical reasons, most functions belonging to this object must be called with the `await` keyword. In addition, any function that contains at least one `await` function must be declared with the `async` keyword.

The use of the `async` and `await` keywords is solely due to the technology used to run *Python* applications in a web browser. They are rarely used in a *Python* program running in a traditional runtime environment, but are indispensable in this context; omitting them will not cause an error, but will prevent applications from working properly.

The `inner` method of the `dom` object (a method is a function attached to an object) is used to replace the contents of a GUI element.

Here, the element is identified by an empty string (`“”`). This identifier is special and designates the entire interface. The entire GUI is thus made up of the contents of the `BODY` constant defined above.

As the `acConnect` function calls the *atlastk* module, but also uses the contents of the `BODY` constant, it will be placed as follows:

<div class="example">
<pre>
import atlastk
<span></span>
BODY = """
&lt;fieldset>
  &lt;input placeholder="Name" value="World">
  &lt;button>Send&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Display area&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""
<div class="todo">
async def acConnect(dom):
  await dom.inner("", BODY)
</div></pre>
</div>

### Association display function / new connection (`CALLBACKS`)

We're now going to associate this function with an action, in this case the one corresponding to a new connection. To do this, we'll define a constant named `CALLBACKS`, which will look like this:

<div class="example">
<pre class="todo">
CALLBACKS = {
  "": acConnect,
}
</pre>
</div>

`CALLBACKS` is what we call a dictionary, allowing us to associate an action identified by the empty string (`“”`) with the `acConnect` function defined above. The empty string, in this context, identifies the action associated with a new connection.

Now let's call the function that will handle all this:

<div class="example">
<pre class="todo">
atlastk.launch(CALLBACKS);
</pre>
</div>

`atlastk` refers to the previously imported module of the same name and `launch` is one of its functions to which we pass, in this case, the previously defined `CALLBACKS` constant. It is this function that will launch the rendering of the interface and handle the user's interactions with the interface as defined in `CALLBACKS`.

Below you'll find all the code developed so far:


<pre data-type="sandbox">
import atlastk

BODY = """
&lt;fieldset>
  &lt;input placeholder="Name" value="World">
  &lt;button>Send&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Display area&lt;/output>
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

Clicking on *Run* will display the interface as elaborated on the [*Interface*](../frontend) page. However, clicking on the *Send* button will have no effect, as the part of the code that supports this action is missing. It's this code that we're now going to develop.

## Handling the *Send* button

### Association click on *Send* button / action (`xdh:onevent=“Submit”`)

Let's modify the application code to indicate which action to associate with the clicking on the *Send* button. To do this, we'll update the *HTML* code:

<div class="example">
<pre>
BODY = """
&lt;fieldset>
  &lt;input placeholder="Name" value="World">
  &lt;button <span class="todo">xdh:onevent="Submit"</span>>Send&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Display area&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""
</div>

With this code (`xdh:onevent=“Submit”`), we add an attribute to the *HTML* element `button`. For each *HTML* element, as we saw on the [*Interface*](../frontend) page, we can specify a series of predefined attributes. But you can also *extend* *HTML* and create your own attributes (and elements too). These extensions to *HTML* code must be specified within a namespace. Here, the namespace is `xdh` and the `:` means that the identifier that follows (`onevent`) belongs to this namespace.

When parsing this code, the web browser, which is responsible for rendering *HTML* code, will ignore anything that belongs to a namespace it doesn't know. It's the *atlastk* module which, when parsing the *HTML* code in turn, detects the presence of components associated with the `xdh` namespace and will handle them.

Here, the attribute is `xdh:onevent` and its value is `Submit`. This means that the default action of the given button (clicking on it) is associated with an event named `Submit`.

Let's take a look at the code in full:

<pre data-type="sandbox">
import atlastk

BODY = """
&lt;fieldset>
  &lt;input placeholder="Name" value="World">
  &lt;button xdh:onevent="Submit">Send&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Display area&lt;/output>
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

The application now displays the interface as before, but this time a click on the *Send* button causes an error message to be displayed. This indicates that a *Submit* action has been associated with the click on the *Send* button, but that there is no code associated with this action.

Let's fix that.

### Function associated with the *Send* button (`acSubmit`)

For didactic purposes, clicking on the button will, at first, simply display a message indicating that the click has been taken into account.

Here's what the code will look like:

<div class="example">
<pre class="todo">
async def acSubmit(dom):
  await dom.alert('Clic sur le bouton "Envoyer" détecté !')
</pre>
</div>

We find again the various elements (`async`, `await`, parameter `dom`...) we discovered with the `acConnect` function. The `alert` method of the object corresponding to parameter `dom` displays a dialog box containing the string passed as parameter.

### Association function `acSubmit` / action `Submit` (`CALLBACKS`)

We'll now associate this function with the `Submit` action by modifying the `CALLBACKS` constant as follows:


<div class="example">
<pre>
CALLBACKS = {
  "": acConnect,
<span class="todo">  "Submit": acSubmit,</span>
}
</pre>
</div>

Here is the complete code:

<pre data-type="sandbox">
import atlastk

BODY = """
&lt;fieldset>
  &lt;input placeholder="Name" value="World">
  &lt;button xdh:onevent="Submit">Send&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Display area&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""

async def acConnect(dom):
  await dom.inner("", BODY)

async def acSubmit(dom):
  await dom.alert('Click on the "Send" button detected!')

CALLBACKS = {
  "": acConnect,
  "Submit": acSubmit,
}

atlastk.launch(CALLBACKS)
</pre>

This time, clicking on the `Send` button displays the expected message (*Click on the `Send` button detected!*).

Let's finalize the `acSubmit` function.

## Retrieving of user data

### Input field identification for content retrieval (`id=“Input”`)

Let's modify the *HTML* code to add an identifier to the input field in order to retrieve its content:

<div class="example">
<pre>
BODY = """
&lt;fieldset>
  &lt;input placeholder="Name" value="World" <span class="todo">id="Input"</span>>
  &lt;button xdh:onevent="Submit">Send&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Display area&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""
</div>

The `id` attribute is used to assign an identifier to an *HTML* element so that it can be referred to, as we'll see later. This identifier must, of course, be unique among all the elements making up a *HTML* document.

### Retrieving the content of a *HTML* element (`dom.getValue(...)`)

Let's modify the `acSubmit` function to retrieve the content of the input field and display it in the dialog box:

<div class="example">
<pre>
async def acSubmit(dom):
<span class="todo">  input = await dom.getValue("Input")</span>
<span class="old">  await dom.alert('Click on tne "Send" button detected!')</span>
<span class="todo">  await dom.alert(f'Value of input field: "{input}"')</span>
</pre>
</div>

The `getValue(...)` method retrieves the value of an *HTML* element, in this case that of identifier `Input` corresponding to the input field. The code `input = …` is used to assign this value to the variable of identifier `input`.

The character string given as a parameter to the `alert(...)` method, because it is preceded by the `f` character, is an *f-string* and therefore undergoes special treatment. Indeed, any expression between braces (`{}`) present in an *f-string* is evaluated. In our case, the string contains the expression `{input}`. This expression will be replaced by the contents of the `input` variable when the application is run, i.e., as previously indicated, by the contents of the input field.

Let's test the code with all the modifications:

<pre data-type="sandbox">
import atlastk

BODY = """
&lt;fieldset>
  &lt;input placeholder="Name" value="World" id="Input">
  &lt;button xdh:onevent="Submit">Send&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Display area&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""

async def acConnect(dom):
  await dom.inner("", BODY)

async def acSubmit(dom):
  input = await dom.getValue("Input");
  await dom.alert(f'Value of input field: "{input}"')

CALLBACKS = {
  "": acConnect,
  "Submit": acSubmit,
}

atlastk.launch(CALLBACKS)
</pre>

When you click on the *Send* button, the dialog box displays the value retrieved from the input field (*World*).

## Displaying content in the interface

### Display zone identification (`id=“Output”`)

As with the input zone, we'll assign the element corresponding to the display zone its own identifier (`Output`):

<div class="example">
<pre>
BODY = """
&lt;fieldset>
  &lt;input placeholder="Name" value="World" id="Input">
  &lt;button xdh:onevent="Submit">Send&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output <span class="todo">id="Output"</span>>Display area&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""
</pre>
</div>

### Modifying the content of an *HTML* element (`dom.setValue(...)`)

Let's alter the `acSubmit` function to modify the content of the display zone to show a text containing the data entered by the user, which is stored in the `input` variable:

<div class="example">
<pre>
async def acSubmit(dom):
  input = await dom.getValue("Input")
<span class="old">  await dom.alert(f'Value of input field: "{input}"')</span>
<span class="todo">  await dom.setValue("Output", f'Hello, {input}!')</span>
</pre>
</div>

The `setValue(...)` method is used to modify the value of an *HTML* element, in this case that of identifier `Output`, with the character string passed as parameter.

Let's test the code with all the modifications:


<pre data-type="sandbox">
import atlastk

BODY = """
&lt;fieldset>
  &lt;input placeholder="Name" value="World" id="Input">
  &lt;button xdh:onevent="Submit">Send&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output id="Output">Display area&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""

async def acConnect(dom):
  await dom.inner("", BODY)

async def acSubmit(dom):
  input = await dom.getValue("Input");
  await dom.setValue("Output", f'Hello, {input}!')

CALLBACKS = {
  "": acConnect,
  "Submit": acSubmit,
}

atlastk.launch(CALLBACKS)
</pre>

Clicking on the *Send* button displays a greeting message containing the text in the input field. You can perform a few more tests by changing the content of this input field.

## Improved ergonomics

### Focus on an *HTML* element (`dom.focus(...)`)

You'll notice that after clicking the *Send* button, you'll need to click in the input field to be able to make a new entry. The input field is said to “lose focus”. On a smartphone, pressing the *Send* button closes the virtual keyboard.

An element is said to have the focus when it is the target of the user's actions. So, when the input zone has the focus, it's in this zone that the characters entered on the keyboard appear.

Let's modify the code so that the input zone regains focus each time the input is validated, as well as when a session is opened. To do this, we modify the `acConnect` and `acSubmit` functions:


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

The `focus(…)` method is used to give focus to the element whose identifier is passed as a parameter. Note that only one element (or none at all) can have the focus at any given time.

Let's test the result:

<pre data-type="sandbox">
import atlastk

BODY = """
&lt;fieldset>
  &lt;input placeholder="Name" value="World" id="Input">
  &lt;button xdh:onevent="Submit">Send&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output id="Output">Display area&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""

async def acConnect(dom):
  await dom.inner("", BODY)
  await dom.focus("Input")

async def acSubmit(dom):
  input = await dom.getValue("Input");
  await dom.setValue("Output", f'Hello, {input}!')
  await dom.focus("Input")

CALLBACKS = {
  "": acConnect,
  "Submit": acSubmit,
}

atlastk.launch(CALLBACKS)
</pre>

On launch, the cursor blinks in the input field, indicating that it has focus. On *Android* or *iOs* devices, depending on the browser you're using, you'll still need to click in the input field to enter text (displaying of the virtual keyboard), but once you've clicked on *Send*, the virtual keyboard will remain open and you'll be able to enter text without having to click on the input field first.

### Bonus

We're going to make two more small modifications using some of the elements we've already used. The first is in the *HTML* code, so that you can validate the entered data directly with the *Enter* key on a physical or virtual keyboard, and the second is in the code for the `acSubmit` function, to empty the input field after each validation, clearing the way for a new entry.

These changes are as follows:


<div class="example">
<pre>
BODY = """
&lt;fieldset>
  &lt;input id="Input" <span class="todo">xdh:onevent="Submit" </span>placeholder="Name" value="World">
  &lt;button xdh:onevent="Submit">Send&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output>Display area&lt;/output>
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

Let's see what happens:

<pre data-type="sandbox">
import atlastk

BODY = """
&lt;fieldset>
  &lt;input id="Input" xdh:onevent="Submit" placeholder="Name" value="World">
  &lt;button xdh:onevent="Submit">Send&lt;/button>
  &lt;hr>
  &lt;fieldset>
    &lt;output id="Output">Display area&lt;/output>
  &lt;/fieldset>
&lt;/fieldset>
"""

async def acConnect(dom):
  await dom.inner("", BODY)
  await dom.focus("Input")

async def acSubmit(dom):
  input = await dom.getValue("Input");
  await dom.setValue("Output", f'Hello, {input}!')
  await dom.focus("Input")
  await dom.setValue("Input", "")

CALLBACKS = {
  "": acConnect,
  "Submit": acSubmit,
}

atlastk.launch(CALLBACKS)
</pre>

Note that you can now use the *Enter* key on the physical or virtual keyboard to validate your input, and that the input field empties after each validation.

## Going on

The [*Inspiration*](../.../inspiration) section offers a whole range of applications for discovering new functionalities, which you can launch and modify *in situ* to explore how they work.  
The [*Create*](../../create) section is dedicated to creating your own applications.

<!-- Helpers -->


<link rel="stylesheet" type="text/css" href="/backend.css"/>
<script src="/backend.js"></script>

<script>
  buildBackendSandboxes("Show/hide", "Open in new tab")
</script>

