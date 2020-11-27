- When using CRA, the babel config is handled by webpack config file. 
So when you create `.babelrc` file in the root, maybe it wouldn’t work unless you configured `babel-loader`.

- When using babel-loader, set the option of `.babelrc` will do that:
    - If true, the plugins of `.babelrc` will replace the babel-loader’s plugins, but the presets will be merged even if false.
    - If false, the plugins of `.babelrc` will not work.
    
- The `exit` property of babel types, its params include the code that compiled by presets and plugins
