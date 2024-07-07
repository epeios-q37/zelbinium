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

# The interface

## Introduction

The coding of the interface is based on the *HTML* language, which is made up of tags. If `tag` is the name of the tag, the corresponding opening tag is `<tag>` and the closing tag, `</tag>`. Between the two, we place the tag content, which may itself be made up of tags.

Tags are always nested, i.e. they are closed in the reverse order in which they were opened. If the opening tags are in `<a>` `<b>` `<c>` order, the closing tags must be in order `</c>` `</b>` `</a>`. Any other order, such as `</a>` `</c>` `</b>` for example, is incorrect.

On this page, you can directly enter *HTML* code and see the result displayed in real time. Each time an opening tag is written, the corresponding closing tag is automatically added. In the same way, indentation is automatic. Indentation isn't strictly necessary, but it makes the code much easier to read.

For historical reasons, some tags don't need a closing tag, so they won't be automatically added.

## The box (`fieldset`)

Let's start by displaying a box using the `fieldset` tag:

<div class="example">
  <div class="todo">
&lt;fieldset&gt;
<br/>
&lt;/fieldset&gt;
  </div>
</div>

Click on *Show/Hide* below to display the editor and the preview, and enter the `<fieldset>` characters in the black box. As indicated above, as soon as the `>` character has been entered, the editor will automatically add `</fieldset>`. In addition, the expected box will be drawn in the clear area below the editor.

When you enter a line break, the cursor will go to the line, but will also be set back. This is automatic indentation.

<div data-type="sandbox" data-cursor="1,1">
</div>

The height of the box displayed in the clear area may seem small, but it will adjust to its content, as we'll see below.

Click *Show/Hide* again to save space by hiding the editor and the preview.

## The input field (`input`)

Now let's place an input field for the user, using the `input` tag (the `input` tag is one of those tags that doesn't require a closing tag):

<div class="example">
<div>&lt;fieldset&gt;</div>
<div class="todo">&nbsp;&nbsp;&lt;input&gt;</div>
<div>&lt;/fieldset&gt;</div>
</div>

Enter the white code in the editor, as the greyed-out code is already present.

<div data-type="sandbox" data-cursor="2,3">
<fieldset>
  @
</fieldset>
</div>

A smaller box appears within the existing frame. By clicking on it, we'll see that we can enter text in it; it's therefore an input field available to the user, and we'll see later how to retrieve its contents.

### Input field type (`type=“ ...”`)

There are several types of input fields, which can be specified using the `type` attribute. Here's how to specify a text field:

<div class="example">
<div>&lt;input <span class="todo">type="text"</span>&gt;</div>
</div>

By default, i.e. if we don't supply the `type` attribute, input fields are of text type.

As an example, here's what a *date* input field looks like:

<div data-type="sandbox" data-cursor="1,18">
<input type="date"></input>
</div>

Depending on the type of field, there may be input helpers that appear when you click on certain parts of the field.

Here are some of the other possible values for the `type` attribute: `checkbox`, `color`, `file`, `radio`, `range`.... You can replace the `date` value of the `type` attribute in the editor above with one of these values to see the effects.

### Hint text (`placeholder=“ ...”`)

Text input fields allow you to specify a text to be displayed when the field is empty, in order to provide an hint as to its contents. This is done using the `placeholder` attribute. For example, here's the code indicating that the text input field above is intended to collect the user's name:

<div class="example">
<div>&nbsp;&nbsp;&lt;input <span class="todo">placeholder="Name"</span>&gt;</div>
</div>

Let's see the result:

<div data-type="sandbox" data-cursor="1,18">
<input placeholder="Name"></input>
</div>

You'll notice that, as soon as you start entering text in the input area, the hint text disappears.

### Default value (`value=“...”`)

Thanks to the `value` attribute, it's possible to pre-fill a text input field, which can facilitate application debugging. 

And the result:

<div data-type="sandbox" data-cursor="1,18">
<input value="World">
</div>

An *HTML* element can have several attributes. Their order is unimportant (`<input placeholder=“Name” value=“World”>` is equivalent to `<input value=“World” placeholder=“Name”>`), but each of its attributes must be unique, whatever its value.

## The button (`button`)

Let's add a button with the `button` tag:

<div class="example">
<div>&lt;fieldset&gt;</div>
<div>&nbsp;&nbsp;&lt;input placeholder="Name" value="World"&gt;</div>
<div class="todo">&nbsp;&nbsp;&lt;button&gt;Send&lt;/button&gt;</div>
<div>&lt;/fieldset&gt;</div>
</div>

The button label (here *Send*) must be placed between the opening and closing tags.

<div data-type="sandbox" data-cursor="3,3">
<fieldset>
  <input placeholder="Name" value="World">
  @
</fieldset>
</div>

## The separator (`hr`)

Now let's add a separator between the input part of the interface and the display part. This is achieved using the `hr` tag:

<div class="example">
<div>&lt;fieldset&gt;</div>
<div>&nbsp;&nbsp;&lt;input placeholder="Name" value="World"&gt;</div>
<div>&nbsp;&nbsp;&lt;button&gt;Send&lt;/button&gt;</div>
<div class="todo">&nbsp;&nbsp;&lt;hr&gt;</div>
<div>&lt;/fieldset&gt;</div>
</div>

The `hr` tag is also a tag that does not require a closing tag.

<div data-type="sandbox" data-cursor="4,3">
<fieldset>
  <input placeholder="Name" value="World">
  <button>Send</button>
  @
</fieldset>
</div>

## The display area (`fieldset` & `output`)

We'll finish with a display area delimited by a box, using the `output` tag embedded in a `fieldset` tag:

<div class="example">
<div>&lt;fieldset&gt;</div>
<div>&nbsp;&nbsp;&lt;input placeholder="Name" value="World"&gt;</div>
<div>&nbsp;&nbsp;&lt;button&gt;Send&lt;/button&gt;</div>
<div>&nbsp;&nbsp;&lt;hr&gt;</div>
<div class="todo">&nbsp;&nbsp;&lt;fieldset&gt;</div>
<div class="todo">&nbsp;&nbsp;&nbsp;&nbsp;&lt;output&gt;Display area&lt;/output&gt;</div>
<div class="todo">&nbsp;&nbsp;&lt;/fieldset&gt;</div>
<div>&lt;/fieldset&gt;</div>
</div>

As the `output` tag is nested within the `fieldset` tag, its indentation is doubled.

<div data-type="sandbox" data-cursor="5,3">
<fieldset>
  <input placeholder="Name" value="World">
  <button>Send</button>
  <hr>
  @
</fieldset>
</div>

We're now going to use this code in the [*Processing*](../backend) page; which will deal with the coding of interactions between the user and the interface.

<!-- Helpers -->


<link rel="stylesheet" type="text/css" href="/frontend.css"/>
<script src="/frontend.js"></script>

<script>
  buildFrontendSandboxes("Show/hide");
</script>
