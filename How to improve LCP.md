## [[Loading Sequence]] Optimization
1. External CSS resources have been finished loading
2. There is no synchronous JavaScript
3. The largest image resources are ready
4. There are no tasks causing render or main thread blocking.
5. Awaiting the browser to render the images onto the screen.

![[begin-render.png]]

## [[Above The Fold]]
Portion of a webpage that is visible without scrolling, typically the content that appears immediately when you first load the page

![[above-the-fold.png]]

## Preload resources(images) that above the fold
Using preload helps here because the image starts loading ahead of time and is likely to already be there when the browser needs to display it.
```html
<link rel="preload" 
	  as="image" 
	  href="banner.png"
	  imagesrcset="banner-400.png 400w, banner-1600.png 1600w"
	  imagesizes="90vw"
>
```
#### With Next.js
```jsx
import Image from 'next/image'

<Image src="banner.png" alt="" priority={true} />
```
### Note
Don't switch image url on client side -> SPA
```jsx
function Banner(){
	const [imageUrl, setImageUrl] =useState('mobile.png')

	const isMobile = useMediaQuery('max-width: 768')
	
	useEffect(() => {
		setImageUrl(isMobile)
	},[])

	return (
		<img src={imageUrl} alt='banner'/>
	)
}
```

### Ref
Must Read - [A deep dive into optimizing LCP](https://www.youtube.com/watch?v=fWoI9DXmpdk)
