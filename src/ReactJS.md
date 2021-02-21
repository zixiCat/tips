- If you would like to use .svg files in React Component, you can do it as following...[ref](https://stackoverflow.com/questions/42296499/how-to-display-svg-icons-svg-files-in-ui-using-react-component)
	```JavaScript
	import { ReactComponent as YourSvg } from './your-svg.svg';

	const App = () => (
	  <div>
	    <YourSvg />
	  </div>
	);
	```
- We should not wrap every prop with useCallback or useMemo...[ref](https://stackoverflow.com/questions/55310682/should-i-wrap-every-prop-with-usecallback-or-usememo-when-to-use-this-hooks)
- The difference between `useMutationEffect` and `useLayoutEffect`...[ref](https://stackoverflow.com/questions/53513872/react-hooks-what-is-the-difference-between-usemutationeffect-and-uselayoutef)
