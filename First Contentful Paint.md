The time it takes from loading a webpage to displaying any content on the webpage (text, images, SVG, canvas) on the screen.
![[first-content.png]]


## [[How to improve FCP]]
#### [[Server Side Render]]
To speed up the FCP, we utilize Next.js [[Server Side Render]] for pre-rendering HTML instead of a SPA like React since the page content must be rendered after JavaScript execution

#### [[When does the browser begin rendering]]
And you also need to consider strategy like [[Non-blocking JS, CSS]]