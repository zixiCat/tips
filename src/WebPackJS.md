- Use `speed-measure-webpack-plugin` to measure building speed
- Do not create an entry for vendors or other stuff that is not the starting point of execution, `optimization.splitChunks` helps you...[ref](https://webpack.js.org/concepts/entry-points/#entrydescription-object)
