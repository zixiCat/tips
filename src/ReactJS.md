- If you would like to use .svg files in React Component, you can do it as following...[ref](https://stackoverflow.com/questions/42296499/how-to-display-svg-icons-svg-files-in-ui-using-react-component)
	```JavaScript
	import { ReactComponent as YourSvg } from './your-svg.svg';

	const App = () => (
		<div>
			<YourSvg />
		</div>
	);
	```
