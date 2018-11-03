# Project-7-Codepath

#1: Authenticated Stored Cross-Site Scripting (XSS)

This exploit requires an attacker to have an account with posting capabilities (i.e. a minimum of Contributor level permissions). In this vulnerability, an attacker can insert arbitrary Javascript via a specially-crafted shortcode onto a page or a post.

Recreating the Exploit

Gain access to an account with at least posting-level permissions via social engineering or another exploit. (Alternatively, if the site allows unauthenticated users to post via some special configuration, then an account is not needed.)
Either create a new page/post or modify an existing one.
Use the HTML editor (not the Visual editor) to insert code similar to the following and post:
<a href="[caption code=">]</a><a title=" <Event-attribute-with-JS-code-here>  ">link</a>
which WP processes to:

<a href="</a><a title=" <Event-attribute-with-JS-code-here> ">link</a>
Example

If an attacker puts in the following:

<a href="[caption code=">]</a><a title=" onmouseover=alert('XSS!')  ">link</a>
WP processes this to become:

<a href="</a><a title=" onmouseover=alert('XSS!') ">link</a>
Here, the closing of the first a tag and the opening of the second a tag are caught up in the first a tag's href attribute, which means that the first a tag now has an href attribute and an onmouseover attribute (the latter of which executes our JS code). So, when the post/page is opened and a user mouses over this (fake) link, the browser shows an alert box with the word "XSS." Of course, one could replace this JS code with something far more malicious.
