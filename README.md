This is a rollup plugin that polyfills ESM imports with CSS type assertions, allowing JS modules to import CSS modules as `CSSStyleSheet` objects that can be adopted as constructed stylesheets.

Of course, this doesn't extend network functionality, but rather inlines the CSS text of the imported file as a constructed stylesheet. So this still doesn't come with most native module benefits (caching, tree shaking, etc.) Instead it's intended as an eventual "drop and forget" plugin once the native feature becomes widely available (~a year from now at best, probably).

As of July 2025, this feature is not natively widely available across browsers. Chromium has shipped it, but still only as of very recent versions. Firefox has marked it "worth prototyping" with no set priority since 4 years ago (see https://bugzilla.mozilla.org/show_bug.cgi?id=1720570). Same for Safari (see https://bugs.webkit.org/show_bug.cgi?id=227967).
