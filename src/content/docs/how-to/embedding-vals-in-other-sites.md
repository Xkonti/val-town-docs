---
title: Embed
generated: 1701279907755

---

Vals are made to be shared, and not just on val.town!

## Embedding an existing val

You can embed any public or unlisted val on another site by copying the embed
URL from the val menu.

![Untitled](./embedding-vals-in-other-sites/untitled.png)

### Embedding in WYSIWYG editors

When writing for the web, lots of people use WYSIWYG editors, such as those in
Wordpress or Notion. In tools with a simple writing experience, you can paste
your embed URL straight in. Here’s how it looks when pasted into Notion (which
generates this page):

<div class="not-content">
  <iframe src="https://www.val.town/embed/neverstew.embedded" width="100%" frameborder="no" style="height: 400px;">
    &#x20;
  </iframe>
</div>

In other editors, you might have to create an “embed” and paste the URL into the
form that the tool provides.

### Embedding in HTML

For sites that don’t provide an editing experience as smooth as Notion or
Wordpress, you can embed your val using an
[iframe](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)
element.

Here’s an example, using a web page created by a val that embeds itself:

<div class="not-content">
  <iframe src="https://www.val.town/embed/neverstew.embedSelf" width="100%" frameborder="no" style="height: 400px;">
    &#x20;
  </iframe>
</div>

And here’s the final web page:

[https://neverstew-embedself.web.val.run/](https://neverstew-embedself.web.val.run/)

## Embedding a new val template

In some scenarios, especially those where you’re providing a guide or a post
that the reader is following along with, it’s useful to provide a template for
your readers to fork. You can do that using the
[https://val.town/embed/new](https://val.town/embed/new) endpoint. To generate a
new val:

1. visit [https://val.town/embed/new](https://val.town/embed/new)
2. type the code that you want to appear
3. copy the new URL of the page you are on

Here’s an example:

<div class="not-content">
  <iframe src="https://www.val.town/embed/new?code=const+myNewEmbeddedVal+%3D+%60The+time+this+ran+was+%24%7Bnew+Date%28%29.toLocaleTimeString%28%29%7D%60%3B" width="100%" frameborder="no" style="height: 400px;">
    &#x20;
  </iframe>
</div>

The URL contains the fragment of code that populates the embed. For example, for
the embed above, the URL you would use is
[https://www.val.town/embed/new?code=const+myNewEmbeddedVal+%3D+`The+time+this+ran+was+%24{new+Date().toLocaleTimeString()}`%3B](https://www.val.town/embed/new?code=const+myNewEmbeddedVal+%3D+%60The+time+this+ran+was+%24%7Bnew+Date%28%29.toLocaleTimeString%28%29%7D%60%3B)