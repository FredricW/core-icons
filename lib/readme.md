# Core Icons

## Icon and logo kit providing a consistent and predictable user experience across platforms and NRK services

---

## Installation
[Download the full kit](https://github.com/nrkno/core-icons/archive/master.zip) for sketching, [individual SVGs](#icons) for Android, [PDFs](#icons)
for iOS. As [SVG symbols](https://css-tricks.com/svg-symbol-good-choice-icons/) can not can load cross domain, or from external file and in IE (9,10,11), `@nrk/core-icons` provides a cacheable, cross-domain [Javascript API](#javascript-api) and [React API](#react-api). All icons follow [BEM naming conventions](http://getbem.com/) and are prefixed with `nrk-` to play nice with existing code.

```bash
npm install @nrk/core-icons --save  # Use from NPM
```
```html
<!-- Use from static.nrk.no: insert just before </body> -->
<script async src="https://static.nrk.no/core-icons/major/5/core-icons.min.js"></script>
```

---

## Scaling

Since logos do not have consistent dimensions, `@nrk/core-icons` provides scaling based on `font-size`.
Scale the icons/logos by using font sizes divisible with `10` for sharpest rendering. Example: `font-size: 10px` = `15×15` icon, `font-size: 20px` = `30×30` icon, etc.

✅ Do | 🚫 Don't
:-- | :--
`.parent { font-size: 10px }` | `.parent svg { width: 30px; height: 30px }`
<div>`<div class="parent"><svg style="width:1.5em;height:1.5em">…`</div> | `<div class="parent"><svg style="width:30px;height:30px">…`

<small>Note: correct width/height in `em` for each icon is automatically provided by `@nrk/core-icons`</small>

---

## Icons

<label class="nrk-button">
  <span class="nrk-sr">Filter icons</span>
  <input type="text" name="search" placeholder="Type to search" class="nrk-unset">
</label><label class="nrk-button">
  <span>Choose color</span>
  <input type="color" name="color" class="nrk-sr" value="#000000">
</label>
<div class="docs-icons nrk-grid" style="padding:0 7vw;margin:0 -7vw;transition:.2s"></div>
<script src="pdfkit-and-blob-stream.js"></script>
<script src="core-icons.min.js"></script>
<script src="docs.js"></script>

---

## Accessibility

Modern versions of assistive technologies will announce SVG content, but there is still a lot of differences between browsers. To avoid confusion, use the following conventions:

<div class="nrk-grid">
  <div class="nrk-xs-12of12 nrk-md-4of12" style="padding-right:15px">
    <div class="doc-demo">
      <a href="https://nrk.no/">
        Gå til nrk.no
        <svg aria-hidden="true" width="30" height="15"><use xlink:href="#nrk-arrow-right-long" /></svg>
      </a>
    </div>
    <h3>Icon used as decoration</h3>
    Use the <code>aria-hidden="true"</code> attribute to hide the icon from screen readers while keeping it visually perceivable.
  </div>
  <div class="nrk-xs-12of12 nrk-md-4of12" style="padding-right:15px">
    <div class="doc-demo">
      <a aria-label="Gå til nrk.no" href="https://nrk.no/">
        <svg aria-hidden="true" width="3.5em" height="1em"><use xlink:href="#nrk-logo-nrk" /></svg>
      </a>
    </div>
    <h3>Clickable icon</h3>
    Add screen reader content to the clickable element (<code>button</code> or <code>a</code>) with <code>aria-label="…"</code>, and hide the icon from screen readers with <code>aria-hidden="true"</code>
  </div>
  <div class="nrk-xs-12of12 nrk-md-4of12" style="padding-right:15px">
    <div class="doc-demo">
      <span role="img" aria-label="Terningkast seks">
        <span class="nrk-sr">Terningkast seks</span>
        <svg aria-hidden="true" style="width:1.5em;height:1.5em;vertical-align:middle"><use xlink:href="#nrk-dice-6--active" /></svg>
      </span>
      Fantastisk!
    </div>
    <h3>Non-clickable icon</h3>
    Hide the icon from screen readers with <code>aria-hidden="true"</code>, and add screen reader content to a wrapper with <code>role="img" aria-label="…"</code>, as well as inside a <code>.nrk-sr</code>.
  </div>
</div>

---

## Javascript API

*NB: requires tree shaking*. `@nrk/core-icons` exposes icons as individually exported constants (enabling [tree shaking](https://medium.com/@netxm/what-is-tree-shaking-de7c6be5cadd)) when included as a NPM module:

```js
import {nrkLogoNrk} from '@nrk/core-icons'

nrkLogoNrk // Is a HTML string of <svg>…</svg>
```

---

## React API
*NB: requires tree shaking*. `@nrk/core-icons` provides a React/Preact API:

```js
import {NrkLogoNrk} from '@nrk/core-icons/core-icons.jsx'

<NrkLogoNrk />                          // Render a NRK logo
<NrkLogoNrk style={{color: 'red'}} />   // Additional props will be used for attributes
```
