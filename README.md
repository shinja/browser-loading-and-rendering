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

# References
- https://hacks.mozilla.org/2017/09/building-the-dom-faster-speculative-parsing-async-defer-and-preload/