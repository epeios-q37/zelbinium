---
title: Create
menu: Create
weight: 5
---

<!--
Si URL modifiée, adapter :
- tutorial/backend
-->

# Create your own application

Here you can create your own application.

A tutorial on creating an interface is available on the [*Interface*](../tutorial/frontend) page of the [*Tutorial*](../tutorial) section, and another on coding the processing part on the [*Processing*](../tutorial/backend) page of the same *Tutorial* section.


In the insert below, we'll draw the application interface. Once this has been done, we'll move on to the second insert.


<div id="Frontend" data-cursor="1,1">
<!-- To replace with the HTML code of your interface. -->
</div>

<br/>

In the insert below, replace the content of the `BODY` constant with the content created above. Add the desired features and click *Run* to launch the application.

<pre id="Backend" data-cursor="4,1">
import atlastk

BODY = """
&lt;center>
&lt;h5>To replace with the HTML code corresponding to your interface.&lt;/h5>
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
  buildFrontendSandbox(document.getElementById("Frontend"), "Show/hide interface");

  appendBrythonInNewTabCode();

  buildBackendSandbox(document.getElementById("Backend"), "Show/hide application", "Open in new tab");
</script>
