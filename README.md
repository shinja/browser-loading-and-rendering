# CSS Block Rendering

## Watch Performance in DevTools

- Parse HTML -> send request -> receving response
- Parse Stylesheet -> finish loading
- Parse HTML -> Recalculate Style -> DCL(DOMContentLoaded)
- Loading external resource (Non-block rendering)

# JS Block Parsing HTML

- What is the difference after we have `<script>` tag in html?
    - Parse HTML process will be blocked after we encounter the `<script>` tag.
    - After executing js, browser resume Parse HTML.
- After the first two CSS files (bootstrap.css and bootstrap-theme.css) are parsed, the downloaded JS could be executed. After JS executed, the remain CSS could be Parsed.

```
Because of this, CSS may block parsing depending on the order of external style sheets and scripts in the document. If there are external style sheets placed before scripts in the document, the construction of DOM and CSSOM objects can interfere with each other. When the parser gets to a script tag, DOM construction cannot proceed until the JavaScript finishes executing, and the JavaScript cannot be executed until the CSS is downloaded, parsed, and the CSSOM is available. [1]
```

## <script async>

- Not guarantee the executing sequence.
- Executed before window `load` event.
## <script defer>

- Guarantee the executing sequence based on load sequence.
- Executed before window `DOMContentLoaded` event.

# Preload

- Chrome
```
Preload decouples fetching a resource from JS processing and execution. As such, preloads declared in markup are optimized in Chrome by the preload scanner. This means that in many cases, the preload will be fetched (with the indicated priority) before the HTML parser has even reached the tag. This makes it a lot more powerful than a custom preload implementation.[2]
```

# References
1. https://hacks.mozilla.org/2017/09/building-the-dom-faster-speculative-parsing-async-defer-and-preload/
2. https://medium.com/reloading/preload-prefetch-and-priorities-in-chrome-776165961bbf