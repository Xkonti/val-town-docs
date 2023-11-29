---
title: Importing modules
generated: 1701279907795
description: Using Val Town's ability to import code from NPM, URLs, and more.
---

Val Town supports importing code from a variety of sources, including
[NPM](https://www.npmjs.com/), [esm.sh](https://esm.sh/), and
[deno.land](https://deno.land/x). You can also import code from arbitrary URLs
if they provide the correct `Content-Type` header and contain JavaScript or
TypeScript.

## Syntax

Through the years, JavaScript has implemented many ways of importing code, so
let's review what's supported by Val Town, and what isn't:

You can use
[static import statements](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import):

```ts
// static-import.ts
import { z } from "npm:zod";
```

You can also use
[dynamic import statements](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/import):

```ts
// dynamic-import.ts
const { z } = await import("npm:zod");
```

We _don’t_ support the old-style `require()` statements popularized as part of
CommonJS.

## Specifiers

We use the Deno runtime, so the way that you import things is
[the same as their documentation](https://docs.deno.com/runtime/manual/basics/modules/):

### NPM Modules

To import an npm module, like [zod](https://www.npmjs.com/package/zod), add
`npm:` in front of the name. So,

```ts
// static-import.ts
import { z } from "npm:zod";
```

### Node builtins

If you want to import a Node.js built-in module, add `node:` in front of its
name. For example, to import the
[crypto](https://nodejs.org/dist/latest-v20.x/docs/api/crypto.html) module, use
this, which is the same as what Node.js themselves officially recommend:

```ts
// static-import.ts
import { createHmac } from "node:crypto";
```

### URLs

To import from a URL, like from esm.sh, you just specify the full url. For
example, to import `zod` but from esm.sh:

```ts
// static-import.ts
import { z } from "https://esm.sh/zod";
```

## Look for examples

Whenever you go to use a new npm library, we recommend first searching to see if
anyone has used that library before.
[You can find the most common packages here](https://www.val.town/examples/packages).

Or you could look for examples related to `cheerio` by searching for it or even
more pointedly
[by searching for `import("npm:cheerio")`](https://www.val.town/search?q=import(%22npm:cheerio%22)).

## Debugging imports

It’s often not clear how a library will expose its methods. It can be helpful to
log the keys of whatever object they return to you. That will tell you if you
need to import it off of default or not, and what is available to you.

<div class="not-content">
  <iframe src="https://www.val.town/embed/stevekrouse.debugCheerioEx" width="100%" frameborder="no" style="height: 300px;">
    &#x20;
  </iframe>
</div>

:::note[Not all modules are compatible with Deno]

Some modules are written with only Node.js or a browser environment in mind, and
won't work with Deno. While Deno implements most of the functionality of Node.js
and some of the functionality of browsers – so many modules will "just work" in
it, some won't.

Also, some modules are written with the assumption that they can access system
resources, compile C code, and more, so they won't work in a secure environment
like Val Town.

As always, ask in our Discord if you want help.

:::