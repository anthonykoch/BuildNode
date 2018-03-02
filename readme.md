# Build node files

Builds js files with node with pre-compile options such as `babel-node`, and `@std/esm`. The `babel-node` build requires running `npm install` in the package directory as well as `npx`. However, [`npx`](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b) already comes pre-installed with npm with version `5.2.0` and higher

## With nvm

Do note that using nvm will increase the build time by ~1.5 seconds.

1. Set a [default alias with](https://eric.blog/2016/08/23/set-default-node-version-with-nvm/) and it will override the system installed node.

2. Update your .bash_profile with [these instructions](https://github.com/SublimeLinter/SublimeLinter/issues/128#issuecomment-129690592) but instead of `stable` use `default`.

If you don't want that message that says `Now using node vx.x.X (npm vx.x.x)` every time you build then add the silent flag as so: `nvm use default --silent`


## Too much clutter in command palette

If you don't want one of the build systems, you can just rename the `.sublime-build` extension to something else so that sublime doesn't recognize the file, or just delete the file.


## Builds

### Node

Simply runs a file with the `node ${file}`.

### ESM

Allows ES6 imports. Calls `node -r @std/esm ${file}`, which uses the version. This will only work if `@std/esm` is installed in the directory the file is being run in.

### Babel

Executes a JS file but first pre-compiles it with babel. Calls `npx babel-node --no-babelrc --extends \"${packages}/BuildNode/.babelrc\" ${file}`. It uses `@babel/preset-env` with the target set to the current version of node. Feel free to change this by [modifying the `.babelrc` in the BuildNode package](https://github.com/anthonykoch/BuildNode/blob/master/.babelrc).

### Nvm Current

Executes a JS file with nvm run, which will use whatever version of node it finds in a `.nvmrc`. Calls `nvm run ${file}`.

**Important:** The instructions above must be followed for this to work properly, or else you'll get an error saying nvm isn't a command.

