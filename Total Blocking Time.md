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