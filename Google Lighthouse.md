# [Does page speed really matter?](https://qwik.builder.io/docs/concepts/think-qwik/#does-page-speed-really-matter)

Put simply: slow sites deter visitors, costing businesses millions. Fast sites have better SEO, better UX, and are more profitable.

---
## PageSpeed insight
2023-08-22
![[initial-2023-08-22.png]]

---
2023-11-22
![[improve-2023-11-22.png]]

### Comparison of Lighthouse scores
|Metric|2023-08-22|2023-11-22|
|---|---|---|
|FCP|3.2s|1.8s|
|LCP|13.3s|2.9s|
|CLS|~0.01|~0.01|
|TBT|9500ms|8000ms|

![[lighthouse-improve.png]]
# Lighthouse Metrics

#### Ranking by weight: TBT > CLS > LCP > FCP
#### Ranking by difficulty: TBT > LCP > FCP > CLS

![[Lighthouse-10.png]]


# [[Calculate Layout Shift]]
In this part, the most important thing is to *fix the width and height* of the element

- Set default width and height for component
```jsx
<div className="placeholder w-[400px] h-[280px] md:w-[1600px] h-[350px]">
	// image
</div>
```


# [[First Contentful Paint]]
The time it takes from loading a webpage to displaying any content on the webpage (text, images, SVG, canvas) on the screen.
![[first-content.png]]

## [[How to improve FCP]]
#### [[Server Side Render]]
To speed up the FCP, we utilize Next.js [[Server Side Render]] for pre-rendering HTML instead of a SPA like React since the page content must be rendered after JavaScript execution

#### [[When does the browser begin rendering]]
After the browser begins parsing HTML, it starts rendering only after the critical CSS resources have been loaded. Consider strategy like [[Non-blocking JS, CSS]]

75kb -> 28kb
![[unused-css.png]]
![[unused-css2.png]]
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
#### Avoid chaining critical requests
#### Avoid large DOM sizes


# [[Largest Contentful Paint]]
The render time of the largest [image or text block](https://web.dev/articles/lcp#what_elements_are_considered) visible within the viewport, relative to when the page [first started loading](https://w3c.github.io/hr-time/#timeorigin-attribute).

![[largest-content.png]]
## [[How to improve LCP]]
#### Preload [[Above The Fold]] resources
Portion of a webpage that is visible without scrolling, typically the content that appears immediately when you first load the page

![[above-the-fold.png]]

#### [[Loading Sequence]] Optimization
1. External CSS resources have been finished loading
2. There is no synchronous JavaScript
3. The largest image resources are ready
4. There are no tasks causing render or main thread blocking.
5. Awaiting the browser to render the images onto the screen.

![[begin-render.png]]

#### [[browser-render-process.canvas|Render Process]]
![[render-process.png]]
#### Ref
[如何改善 LCP](https://web.dev/articles/optimize-lcp#lcp_breakdown)
[A deep dive into optimizing LCP](https://www.youtube.com/watch?v=fWoI9DXmpdk)


# [[Total Blocking Time]]
The most important thing is to minimize unnecessary JavaScript execution on the main thread as much as possible, as well as reducing bundle size.
#### [[Reduce bundle size]]
- Remove unnecessary module
- Choose a lighter-weight package
- Dynamic import component when needed
- Avoid namespace at front-end

- [[Tree Shaking]]
#### Focus on [[Above The Fold]] content
#### Avoid long tasks on main thread
- Reduce hydration cost
- Web Workers
	- Run third party script on web workers, without blocking main thread
### Avoid large DOM sizes
- Instead of load all content initially consider [[Above The Fold]] strategy
- Using React.Fragment

