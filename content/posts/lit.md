---
title: lit
date: 2023-06-18T12:17:27+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1684001217547-17bf9b62931f?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2ODcwNjE2NjB8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1684001217547-17bf9b62931f?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2ODcwNjE2NjB8&ixlib=rb-4.0.3
---

# [lit/lit](https://github.com/lit/lit)

# lit-html
Efficient, Expressive, Extensible HTML templates in JavaScript

[![Build Status](https://github.com/lit/lit/actions/workflows/tests.yml/badge.svg?branch=lit-html-1.x)](https://github.com/lit/lit/actions/workflows/tests.yml?query=branch%3Alit-html-1.x)
[![Published on npm](https://img.shields.io/npm/v/lit-html.svg)](https://www.npmjs.com/package/lit-html)
[![Join our Slack](https://img.shields.io/badge/slack-join%20chat-4a154b.svg)](https://lit.dev/slack-invite/)
[![Mentioned in Awesome Lit](https://awesome.re/mentioned-badge.svg)](https://github.com/web-padawan/awesome-lit)

## Documentation

Full documentation is available at [lit-html.polymer-project.org](https://lit-html.polymer-project.org).

Docs source is in the `docs` folder. To build the site yourself, see the instructions in [docs/README.md](docs/README.md).

## Overview

`lit-html` lets you write [HTML templates](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/template) in JavaScript with [template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals).

lit-html templates are plain JavaScript and combine the familiarity of writing HTML with the power of JavaScript. lit-html takes care of efficiently rendering templates to DOM, including efficiently updating the DOM with new values.

```javascript
import {html, render} from 'lit-html';

// This is a lit-html template function. It returns a lit-html template.
const helloTemplate = (name) => html`<div>Hello ${name}!</div>`;

// This renders <div>Hello Steve!</div> to the document body
render(helloTemplate('Steve'), document.body);

// This updates to <div>Hello Kevin!</div>, but only updates the ${name} part
render(helloTemplate('Kevin'), document.body);
```

`lit-html` provides two main exports:

 * `html`: A JavaScript [template tag](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#Tagged_template_literals) used to produce a `TemplateResult`, which is a container for a template, and the values that should populate the template.
 * `render()`: A function that renders a `TemplateResult` to a DOM container, such as an element or shadow root.

## Installation

```bash
$ npm install lit-html
```

## Forward compatibility with lit-html 2.0

lit-html 2.0 has a new directive authoring API that has been back-ported to lit-html 1.4 in order to ease upgrading.

The lit-html 2.0 directive API is available in new modules whose paths are the same in lit-html 1.4 and 2.0, allowing code to import and use the APIs against either version.

You can import the new APIs like so:

```ts
import {html} from 'lit-html';
import {directive, Directive, Part, PartInfo, PartType} from 'lit-html/directive.js';
```

Then implement a directive class and convert it to a directive function:

```ts
class MyDirective extends Directive {
  // ...
}
/** My directive docs **/
export const myDirective = directive(MyDirective);
```

**Important note:** The `AsyncDirective` base class is available, but lit-html 1.4 does _not_ implement the `disconnected` and `reconnected` callbacks.

For more details on upgrading see the [Update custom directive implementations](https://lit.dev/docs/releases/upgrade/#update-custom-directive-implementations) guide.

## Contributing

Please see [CONTRIBUTING.md](./CONTRIBUTING.md).
