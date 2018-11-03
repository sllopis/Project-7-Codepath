# Project-7-Codepath

#1: Authenticated Stored Cross-Site Scripting (XSS)

Gain access to an account with at least posting-level permissions via social engineering or another exploit. (Alternatively, if the site allows unauthenticated users to post via some special configuration, then an account is not needed.)
Either create a new page/post or modify an existing one.
Use the HTML editor (not the Visual editor) to insert code similar to the following and post:
<a href="[caption code=">]</a><a title=" <Event-attribute-with-JS-code-here>  ">link</a>
which WP processes to:

<a href="</a><a title=" <Event-attribute-with-JS-code-here> ">link</a>
