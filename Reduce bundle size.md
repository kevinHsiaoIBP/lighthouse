#### Dynamic imports
Import component when needed
```jsx
const MobileMenu = dynamic(() => import('./layout/mobile-menu'));
const CartView = dynamic(() => import('./cartView'));
```
Library
- for large weight package
SPA
- by page route

#### Remove unused code or module
webpack config
- [[Tree Shaking]]
preset-env
- reduce polyfill size
unnecessary module
- like import `redis` instance at front-end
lighter-weight package
- like `math.js` to `decimal.js`

#### Cache
vendor bundle
- 讓常用第三方套件被 cache
optional(依專案規模)
- 小專案可將很多人在用的第三方套件使用 CDN version.

---
#### Remove base64 image
```scss
.icon {
    background: url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUg...');
}
```
#### Move static SVG icons to CDN
Folder Structure
	lib
	- icons
		- custom-icons.tsx
		- image-icons.tsx

`custom-icons.tsx`
```jsx
export const ArrowNextBlack = ({ currentSlide, slideCount, ...props }: any) => (
    <div
        {...props}
        className={'slick-next slick-arrow' + (currentSlide === slideCount - 1 ? ' slick-disabled' : '')}
        aria-hidden="true"
        aria-disabled={currentSlide === slideCount - 1 ? true : false}
    >
        <svg
            xmlns="http://www.w3.org/2000/svg"
            width="45"
            height="45"
            viewBox="0 0 24 24"
            fill="none"
            stroke="#000000"
            strokeWidth="1.5"
            strokeLinecap="round"
            strokeLinejoin="round"
        >
            <circle cx="12" cy="12" r="10" />
            <path d="M12 8l4 4-4 4M8 12h7" />
        </svg>
    </div>
);
```

`image-icons.tsx`
```jsx
export const HyteLogo = ({ width = 68, height = 20 }: ISocialMediaIcon) => {
    return <Image src={CDN_ASSETS_URL + 'icons/svg/hyte.svg'} width={width} height={height} alt="hyte" />;
}; 

export function FacebookIcon({ width = 30, height = 30 }: ISocialMediaIcon) {
    return <Image src={CDN_ASSETS_URL + 'icons/svg/facebook.svg'} width={width} height={height} alt="facebook" />;
}

export function TwitterIcon({ width = 30, height = 30 }: ISocialMediaIcon) {
    return <Image src={CDN_ASSETS_URL + 'icons/svg/black_twitter.svg'} width={width} height={height} alt="twitter" />;
}
```

#### Avoid namespace
Don't do this
```jsx
import * as schema from '@/const/seo.schema';
```
```jsx
import React from 'react'

function Component(){
	React.useEffect(() => {
		//
	})
}
```

```jsx
import { useEffect } from 'react'

function Component(){
	useEffect(() => {
		//
	})
}
```

### Ref
[Shubo](https://www.shubo.io/optimize-loading-speed/#code-splittingjs-bundle-%E8%82%A5%E5%A4%A7%E7%9A%84%E6%95%91%E6%98%9F)