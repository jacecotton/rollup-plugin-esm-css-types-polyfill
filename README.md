This is a rollup plugin that polyfills ESM imports with CSS type assertions, allowing JS modules to import CSS modules as `CSSStyleSheet` objects that can be adopted as constructed stylesheets.

Of course, this doesn't extend network functionality, but rather inlines the CSS text of the imported file as a constructed stylesheet. So this still doesn't come with most native module benefits (caching, tree shaking, etc.)

It starts by changing `import ... with {type: "css"}` to `import ...`, so that rollup will bring the text on disk into the importer file. Then, we're instantiating a `new CSSStyleSheet`, and inserting the CSS text with `replaceSync`, then assigning the module reference to that `CSSStyleSheet`.

As of July 2025, this feature is not natively widely available across browsers. Chromium has shipped it, but still only as of very recent versions. Firefox has marked it "worth prototyping" with no set priority since 4 years ago (see https://bugzilla.mozilla.org/show_bug.cgi?id=1720570). Same for Safari (see https://bugs.webkit.org/show_bug.cgi?id=227967).
