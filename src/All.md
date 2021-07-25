# tips

Tips, kind of like notes, is used to record useful tips, my blind spot of knowledge at that time and so on (in continuously update). 

- [BabelJS](https://github.com/zixiCat/tips/blob/master/src/All.md#BabelJS)
- [Bash](https://github.com/zixiCat/tips/blob/master/src/All.md#Bash)
- [CICD](https://github.com/zixiCat/tips/blob/master/src/All.md#CICD)
- [Docker](https://github.com/zixiCat/tips/blob/master/src/All.md#Docker)
- [Git](https://github.com/zixiCat/tips/blob/master/src/All.md#Git)
- [HTML&CSS](https://github.com/zixiCat/tips/blob/master/src/All.md#HTML&CSS)
- [NativeJS](https://github.com/zixiCat/tips/blob/master/src/All.md#NativeJS)
- [NodeJS](https://github.com/zixiCat/tips/blob/master/src/All.md#NodeJS)
- [ReactJS](https://github.com/zixiCat/tips/blob/master/src/All.md#ReactJS)
- [TypeScript](https://github.com/zixiCat/tips/blob/master/src/All.md#TypeScript)
- [VueJS](https://github.com/zixiCat/tips/blob/master/src/All.md#VueJS)
- [WebPackJS](https://github.com/zixiCat/tips/blob/master/src/All.md#WebPackJS)
- [Other](https://github.com/zixiCat/tips/blob/master/src/All.md#Other)

## BabelJS
- When using CRA, the babel config is handled by webpack config file. 
So when you create `.babelrc` file in the root, maybe it wouldn’t work unless you configured `babel-loader`.

- When using babel-loader, set the option of `.babelrc` will do that:
    - If true, the plugins of `.babelrc` will replace the babel-loader’s plugins, but the presets will be merged even if false.
    - If false, the plugins of `.babelrc` will not work.
    
- The `exit` property of babel types, its params include the code that compiled by presets and plugins.
- When using `customize-cra`, to disable babel-loader cache, you can refer to this url...[ref](https://github.com/mixail-novikov/customize-cra-disable-babel-cache)
- JSXText() { … } is shorthand for JSXText: { enter() { … } }

## Bash
- As the code snippet below, We would get the all val from `console.log`
  ```bash
  #!/bin/bash
  VAL=$(node app.js)
  ```
- The different we should know between bash and shell...[ref](https://stackoverflow.com/questions/5725296/difference-between-sh-and-bash)
- Same as NodeJS, we can use color-code to beauty the font...[ref](https://stackoverflow.com/questions/5947742/how-to-change-the-output-color-of-echo-in-linux)
  ```bash
  RED='\033[0;31m'
  NC='\033[0m' # No Color
  echo -e "This is ${RED}red${NC}"
  ```

## CICD
- The official plugin **gitlab-plugin** can help you to send the pipeline result in jenkins to gitlab...[ref](https://github.com/jenkinsci/gitlab-plugin)
- Be aware of the **General** option in repository setting, where you can found some setting about pipeline from **Merge requests**

## Docker
- Seems like you should run two containers, one is jenkins, the other is sub-docker. The sub-docker would help you to run docker in jenkins in docker, and it would help to avoid the error "docker not found"...[ref](https://www.jenkins.io/doc/book/installing/docker/)

## Git
- Use `git stash` to save code temporarily, you could restore it by u1sing `git stash apply index` or `git stash pop index`. Of course there is `git stash list` or `git stash clear`...[ref](https://www.git-scm.com/docs/git-stash)
- Use `git reflog show`, and then you could recover from `git reset --hard` you had done.
- Use this following command line:
  ```bash
  git ls-remote --tags --refs origin | cut -f2 | xargs git push origin --delete
  ```
  Then your all remote tags will be removed in one go, but when you use this command line:
  ```bash
  git tag -l | xargs -n 1 git push --delete origin
  ```
  It will delete remote tags every 2 seconds for one, really trash! The following command line could be used to delete all local tags...[ref](https://stackoverflow.com/questions/19542301/delete-all-tags-from-a-git-repository)
  ```bash
  git tag | xargs git tag -d
  ```
- Use `git reset HEAD@{1}`, and you can recover your code from git-reset-hard, see more...[ref](https://stackoverflow.com/questions/5788037/recover-from-git-reset-hard)
- To authenticate with GitHub, use this one: `https://[USERNAME]:[TOKEN]@[GIT_ENTERPRISE_DOMAIN]/[ORGANIZATION]/[REPO].git`...[ref](https://stackoverflow.com/questions/18935539/authenticate-with-github-using-a-token?answertab=votes#tab-top)
- The similarities and differences between monorepo and polyrepo...[ref](https://github.com/joelparkerhenderson/monorepo_vs_polyrepo)
- Use `git config --local --get core.hookspath`, and then terminal will show the value.
- `git commit -m "subject" -m "body" -m "footer"`
- We can get the committed message via `$(cat $1)` in `commit-msg`, `prepare-commit-msg` of git hooks, but the message isn't accessible to `pre-commit` hook
- To make your committed message awesome, there are some packages to help you like `husky`, `commitizen`. You can also customize hooks files or config the hooksPath to directory you want...[ref](https://backlog.com/blog/git-commit-messages-bold-daring/)
- `git commit -a/--all` will tell the command to automatically stage files that have been modified and deleted, but new files you have not told Git about are not affected...[ref](https://git-scm.com/docs/git-commit/en)

## HTML&CSS
- Use `@font-face` in css file, and you can add custom font file
- The `:root` CSS pseudo-class can help you to declare global variables of CSS
- The CSS function `attr()` would be useful sometimes
- Using `pointer-events: none` in CSS can prevent default event of some element.
- To make the pages that contains `<iframe>` to be adaptive, there is a good way, see lxs's answer...[ref](https://stackoverflow.com/questions/166160/how-can-i-scale-the-content-of-an-iframe)
- `loading` attribute can achieve lazy loading in `<img>` or `<iframe>`...[ref](https://developer.mozilla.org/en-US/docs/Web/Performance/Lazy_loading)

## NativeJS
- `[{a:1, b:2, c:3}] => [{b:2, c:3}]` by `arr.map({a, ...rest} => rest)` 
- If you want every page has the same title when use `window.print()`, you can try to put 'title' to the `<thead>`.
- You can use the @page CSS at-rule to modify the setting of print.
- About JavaScript Style, you can click [this](https://github.com/airbnb/javascript) for more details, followings are some tips I think it's useful for me.
  - Use `const` for all of your references, avoid using `var` or `let`, because this can ensure that you can’t reassign your references, which can lead to bugs and difficult to comprehend code...[ref](https://github.com/airbnb/javascript#references--prefer-const)
  - Do not use `Object.property` directly, such as `hasOwnProperty`. Because these methods may be shadowed by properties on the object in question...[ref](https://github.com/airbnb/javascript#objects--prototype-builtins)
- [optional chaining ?](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining), [nullish coalescing operator ??](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_operator), [logical nullish assignment ??=](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_nullish_assignment)

## NodeJS
- Some packages to beautify style of terminal.
  - [cli-spinners](https://github.com/sindresorhus/cli-spinners)
  - [chalk](https://github.com/chalk/u)
  - [progress](https://github.com/visionmedia/node-progress)
  - [multi-progress](https://github.com/pitaj/multi-progress)
  - [gauge](https://github.com/npm/gauge)
  - [boxen](https://github.com/sindresorhus/boxen)
  - [listr2](https://github.com/cenk1cenk2/listr2)
  - [cli-progress](https://github.com/npkgz/cli-progress)
  - [ora](https://github.com/sindresorhus/ora)
- We can use `process.stderr.write('\x1B[?25h')` to show terminal cursor or use `process.stderr.write('\x1B[?25l')` to hide terminal cursor, that's really useful when it come to beautifying style.
- The `package.json` have some really useful fields that we might use in making npm package, for example, the `bin` field would help you to execute some command via npx, and the `prepare`, `preinstall` in [`script`](https://docs.npmjs.com/cli/v7/using-npm/scripts) filed would help you to run a script when package is installed...see [docs](https://docs.npmjs.com/cli/v7/configuring-npm/package-json) for more details.
- Sometimes you should use the `encoding` option that it would help you to print what you want, e.g. `child_process.execSync("npm info grunt version", { encoding: 'UTF-8'})`.
- In order to interact with terminal, there are some APIs and modules we can use, e.g. `process.openStdin`, `readline`...[ref1](https://stackoverflow.com/questions/5947742/how-to-change-the-output-color-of-echo-in-linux)...[ref2](https://github.com/philipszdavido/cli-select-opts/blob/master/select.js)
- Change color of console.log without package, we can use `console.log('\x1b[32m%s\x1b[0m', 'green')` or `console.log('\x1b[31m', 'red' ,'\x1b[0m')`...[ref](https://stackoverflow.com/questions/9781218/how-to-change-node-jss-console-font-color)
- We can use `git stash` to run bash `scripts` filed in `package.json` via using `bash fileName`...[ref](https://awsm.page/nodejs/run-shell-scripts-using-npm-script/)
- Use `--eval`/`-e`, and then we can run script only in command line...[ref](https://nodejs.org/docs/latest-v15.x/api/cli.html#cli_e_eval_script)
- When the `main` field in `package.json` is set,  use `node .` or `require`  will involve the field as default.

## ReactJS
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


## TypeScript
- You can the following formula to transform union type to intersection type, but don't think it's possible when in the opposite direction.
  ```typescript
  type UnionToIntersection<U> = (U extends any ? (k: U)=>void : never) extends ((k: infer I)=>void) ? I : never
  ```
- You can extract the property name which value is of function type
  ```typescript
  type TFnPropertyNames<T> = { [K in keyof T]: T[K] extends Function ? K : never }[keyof T]
  ```
- If you'd like to set the type of class anyway, you can try this: `type Class<T = any> = new (...args: any[]) => T;`
- If you'd like to the interface that require only one of two property, try this:
  ```typescript
  type RequireOnlyOne<T, Keys extends keyof T = keyof T> = Pick<
    T,
    Exclude<keyof T, Keys>
  > &
    {
      [K in Keys]-?: Required<Pick<T, K>> &
        Partial<Record<Exclude<Keys, K>, undefined>>;
    }[Keys];
  ```
- 6 ways to narrow types in TypeScript...[ref](https://www.carlrippon.com/6-ways-to-narrow-types-in-typescript/)
  - using a conditional value check to remove `null` and `undefined` from a type
  - using `typeof` function to narrow the type to primitive types
  - using `instanceof` function to narrow the type to class types
  - using `in` function to determine if the type is in the object
  - using type predicates to narrow to some complex type you want
  - using `assert` function to narrow to some complex type if you wan throw some errors

- an excellent way to simplify the type `TUnitTransform`, it's related to several key points...[ref](https://stackoverflow.com/questions/65850619/is-there-an-function-to-simplify-the-following-union-type-tunittransform)
  ```typescript
  type TUnitTransform = ((...rest: [number]) => [number]) &
    ((...rest: [number, number]) => [number, number]) &
    ((...rest: [number, number, number]) => [number, number, number]) &
    ......

  type TUnitTransform = 
    <T extends [number, ...number[]]>(...rest: [...T]) => { [K in keyof T]: number; }
  ```

## VueJS
to be continued

## WebPackJS
- Use `speed-measure-webpack-plugin` to measure building speed
- Do not create an entry for vendors or other stuff that is not the starting point of execution, `optimization.splitChunks` helps you...[ref](https://webpack.js.org/concepts/entry-points/#entrydescription-object)

## OTHER
- August 6, 1991: Sir Tim Berners-Lee at CERN launched [the first website](http://info.cern.ch/hypertext/WWW/TheProject.html)
- SHA--Secure Hash Algorithm--安全散列演算法
- When we using 'ping google.com' with ssr running, it would time out, but using vpn can work sometimes. that's as the socks proxy of ssr is based on session layer or transport layer, while vpn is based on network layer, which is the same as `ping operating`...[ref](https://my.oschina.net/u/4330033/blog/4532164)
