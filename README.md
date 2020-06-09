# Highlight JS Web Component

Highlight JS Web Component was created to ease the use of the [Hightlight.js](https://github.com/highlightjs/highlight.js) library.

Highlight-js-wc works by appending the needed style and theme during initialization, eliminating the need to
bundle or build.

[Demo](https://codesandbox.io/s/funny-heisenberg-g30ji?fontsize=14&hidenavigation=1&theme=dark)

### Install

You can use Highlight-js-wc through a CDN or by installing it from npm with

```bash
npm install highlight-js-wc
```

### Usage

You can import the libary through a npm CDN, and use it straight away

```html
<html>
    <head>
        <script type="module" src="https://cdn.jsdelivr.net/npm/highlight-js-wc@1.0.0/highlight-js-wc.min.js"></script>
    </head>

    <body>
        <!-- prettier-ignore -->
        <highlight-js lang="javascript" theme="gruvbox-dark">
addEventListener('load', () => {
  const code = document.querySelector('#code');
  const worker = new Worker('worker.js');
  worker.onmessage = (event) => { code.innerHTML = event.data; }
  worker.postMessage(code.textContent);
});
    </highlight-js>

        <script src="src/index.js" type="module"></script>
    </body>
</html>
```

However if you're using a framwork, it's also easy to use:

```js
import { LitElement, html } from 'lit-element';
import 'highlight-js-wc';

class DemoClass extends LitElement {
    render() {
        // prettier-ignore
        return html`
    <highlight-js lang="javascript">
addEventListener('load', () => {
  const code = document.querySelector('#code');
  const worker = new Worker('worker.js');
  worker.onmessage = (event) => { code.innerHTML = event.data; }
  worker.postMessage(code.textContent);
});
    </highlight-js>
        `;
    }
}
```

### Gotcha's

If you're getting your code formatted weirdly by prettier etc due to the lack of a `<pre>` -tag, you can use the
ignore command of the formatting library to ignore the node in the formatting process.

### TODO

-   Optimize importing process (less is more)
-   Check for language support on all languages
