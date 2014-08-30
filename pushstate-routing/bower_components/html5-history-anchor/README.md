## &lt;a is="html5-history-anchor"&gt;
> Extend the `<a>` tag with the `window.history` API
>
> [HTML5 history spec](http://www.w3.org/html/wg/drafts/html/master/browsers.html#the-history-interface)

The `<a>` tag you know and love.
```html
<a href="/link">A link from 1992</a>
```

Extended with the HTML5 `window.history` API.
```html
<a is="html5-history-anchor" href="/link" pushstate popstate
   title="New Title" state='{"message":"New State!"}'>/link</a>
```

Clicking this link calls the HTML5 history API.
```js
window.history.pushState({message:'New State!'}, 'New Title', '/link');
window.dispatchEvent(new PopStateEvent('popstate', {
  bubbles: false,
  cancelable: false,
  state: {message:'New State!'}
}));
```

`history.pushState()` doesn't dispatch a `popstate` event or load a new page by itself. It was only meant to push state into history. This is an "undo" feature for single page applications. This is why you have to manually dispatch a `popstate` event. Including both `pushstate` and `popstate` attributes on the link will push the new state into history then dispatch a `popstate` event which you can use to load a new page with a router.

## Install
[Download](https://github.com/erikringsmuth/html5-history-anchor/archive/master.zip) or run `bower install html5-history-anchor --save`

## Import
```html
<link rel="import" href="/bower_components/html5-history-anchor/html5-history-anchor.html">
or
<script src="/bower_components/html5-history-anchor/html5-history-anchor.js"></script>
```

## API
The API is a direct extension of the `<a>` tag and `window.history`. Examples:

Call `history.pushState(null, null, '/new-state')` and dispatch a `popstate` event.
```html
<a is="html5-history-anchor" href="/new-state" pushstate popstate>/new-state</a>
```

Call `history.replaceState({message:'Replaced State!'}, null, '/new-state')` but don't `popstate`.
```html
<a is="html5-history-anchor" href="/new-state"
   replacestate state='{"message":"Replaced State!"}'>/new-state</a>
```

Call `history.back()`.
```html
<a is="html5-history-anchor" back>Back</a>
```

Call `history.forward()`.
```html
<a is="html5-history-anchor" forward>Forward</a>
```

Call `history.go(-2)`.
```html
<a is="html5-history-anchor" go="-2">Back 2 Pages</a>
```

Refresh the page with `history.go(0)`.
```html
<a is="html5-history-anchor" go>Refresh</a>
```

## Notes
The [HTML5 history spec](http://www.w3.org/html/wg/drafts/html/master/browsers.html#the-history-interface) is quirky.
- `history.pushState()` and `history.replaceState()` don't dispatch `popstate` events.
- `history.back()`, `history.forward()`, and the browser's back and foward buttons do dispatch `popstate` events.
- `history.go()` and `history.go(0)` do a full page reload and don't dispatch `popstate` events.
- `history.go(-1)` (back 1 page) and `history.go(1)` (forward 1 page) do dispatch `popstate` events.

## Build, Test, and Debug [![Build Status](https://travis-ci.org/erikringsmuth/html5-history-anchor.png?branch=master)](https://travis-ci.org/erikringsmuth/html5-history-anchor)
Source files are under the `src` folder. The build process writes to the root directory. The easiest way to debug is to include the source script rather than the minified HTML import.
```html
<script src="/bower_components/html5-history-anchor/src/html5-history-anchor.js"></script>
```

To build:
- Run `bower install` and `npm install` to install dev dependencies
- Lint, build, and minify code changes with `gulp` (watch with `gulp watch`)
- Start a static content server to run tests (node `http-server` or `python -m SimpleHTTPServer`)
- Run unit tests in the browser (PhantomJS doesn't support Web Components) [http://localhost:8080/tests/SpecRunner.html](http://localhost:8080/tests/SpecRunner.html)
- Manually run functional tests in the browser [http://localhost:8080/tests/functional-test-site/](http://localhost:8080/tests/functional-test-site/)
