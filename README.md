# Project-7-Codepath

**#1: Authenticated Stored Cross-Site Scripting (XSS)**

Recreating the Exploit

1- Gain access to an account with at least posting-level permissions via social engineering or another exploit. (Alternatively, if the site allows unauthenticated users to post via some special configuration, then an account is not needed.)
2- Either create a new page/post or modify an existing one.
3- Use the HTML editor (not the Visual editor) to insert code similar to the following and post:


`<a href="[caption code=">]</a><a title=" <Event-attribute-with-JS-code-here>  ">link</a>`



**#2: Authenticated Shortcode Tags XSS**

Like the last one, this vulnerability also requires the attacker to have an account with posting capabilities. It takes advantage of a shortfall in WordPress's KSES filtering (which filters out non-whitelisted HTML tags).

Recreating the Exploit

Gain access to an account with at least posting-level permissions via social engineering or another exploit. (Alternatively, if the site allows unauthenticated users to post via some special configuration, then an account is not needed.)
Either create a new page/post or modify an existing one.
Use the HTML editor (not the Visual editor) to insert code similar to the following and post:


`[caption width="1" caption='<a href="' ">]</a><a href=" <Event-attribute-with-JS-code-here> ">Click me!</a>`

which WP processes to:

`<figcaption class="wp-caption-text"><a href="</figcaption></figure></a><a href=" <Event-attribute-with-JS-code-here> ">Click me</a>`



**#3: Authenticated Stored XSS in YouTube URL Embeds**

Again, this vulnerability requires at least Contributor level privileges onto the site. Through this exploit, an attacker could take advantage of YouTube URL embeds to achieve a stored/persistent XSS attack that can affect any user who simply loads the compromised page.

Recreating the Exploit

Gain access to an account with at least posting-level permissions via social engineering or another exploit. (Alternatively, if the site allows unauthenticated users to post via some special configuration, then an account is not needed.)
Either create a new page/post or modify an existing one.
Use the HTML editor (not the Visual editor) to insert code similar to the following and post. Here, we demonstrate the vulnerability through the use of an embed shortcode:

`[embed src='https://www.youtube.com/embed/12345\x3csvg <Event-attribute-with-JS-code-here>\x3e'][/embed]`

which WP processes to:

`<p>https://youtube.com/watch?v=12345<svg <Event-attribute-with-JS-code-here>></p>`
