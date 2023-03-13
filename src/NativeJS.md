- `[{a:1, b:2, c:3}] => [{b:2, c:3}]` by `arr.map({a, ...rest} => rest)`
- If you want every page has the same title when use `window.print()`, you can try to put 'title' to the `<thead>`.
- You can use the @page CSS at-rule to modify the setting of print.
- About JavaScript Style, you can click [this](https://github.com/airbnb/javascript) for more details, followings are some tips I think it's useful for me.
  - Use `const` for all of your references, avoid using `var` or `let`, because this can ensure that you can’t reassign your references, which can lead to bugs and difficult to comprehend code...[ref](https://github.com/airbnb/javascript#references--prefer-const)
  - Do not use `Object.property` directly, such as `hasOwnProperty`. Because these methods may be shadowed by properties on the object in question...[ref](https://github.com/airbnb/javascript#objects--prototype-builtins)
- [optional chaining ?](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining), [nullish coalescing operator ??](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_operator), [logical nullish assignment ??=](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_nullish_assignment)
- Please make good use of the second param of `replace` function, in which you can obtain the result of `$1`, `$2`, e.g.
  ```javascript
  'a_bc1'.replace(/_([a-z])([a-z])/g, (x, $1, $2) => $2)
  ```
- You can find a lot of parser tools or transform tools for AST in this site [astexplorer.net](https://astexplorer.net/)
- Browserslist Helps you save time include polyfills manually...[ref](https://stackoverflow.com/questions/55510405/what-is-the-significance-of-browserslist-in-package-json-created-by-create-react)
- When `console.time('lable')` and `console.timeEnd('lable')` use the same label, the console will print this label in front of time
- `RegExp.prototype.toJSON = RegExp.prototype.toString` will Stringify regular expression by `JSON.stringify`
