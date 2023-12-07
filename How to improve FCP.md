#### [[Server Side Render]]
To speed up the FCP, we utilize Next.js [[Server Side Render]] for pre-rendering HTML instead of a SPA like React since the page content must be rendered after JavaScript execution

#### [[When does the browser begin rendering]]
After the browser begins parsing HTML, it starts rendering only after the critical CSS resources have been loaded. Consider strategy like [[Non-blocking JS, CSS]]

### [[What blocks rendering]] ?
All tasks run on the main thread
#### Tasks executed on the main thread
- Resource Loading
- Parsing HTML/CSS
- JavaScript Execution
- DOM Manipulation
- Event Handling (such as clicks, scrolls, and keyboard inputs.)
- Render Tree Construction, Layout, Painting, Compositing

- request animation/rAF
- Web API

#### Preload CSS
Preload important external CSS resource
```html
<link rel="preload" href="/_next/static/css/ccbfa2e8aa325369.css" as="style">
```
#### Font display swap
Show default fonts until custom fonts are fully loaded
```scss
@font-face {
    font-family: 'HCo Gotham SSm';
    src: url('./woff2/GothamSSm-XLight_Web.woff2') format('woff2'),
        url('./woff/GothamSSm-XLight_Web.woff') format('woff');
    font-weight: 200;
    font-style: normal;
    font-display: swap;
}
```
#### Avoid [[chaining critical requests]]
#### Avoid large DOM sizes