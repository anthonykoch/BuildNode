# Build node files

Builds js files with node with pre-compile options such as `babel-node`, and `@std/esm`. The `babel-node` build requires running `npm install` in the package directory.

## With nvm

Do note that using nvm will increase the build time by ~1.5 seconds.

1. Set a [default alias with](https://eric.blog/2016/08/23/set-default-node-version-with-nvm/) and it will override the system installed node.

2. Update your .bash_profile with [these instructions](https://github.com/SublimeLinter/SublimeLinter/issues/128#issuecomment-129690592) but instead of stable use `default`.

If you don't want that message that says `Now using node vx.x.X (npm vx.x.x)` every time you build then write `nvm use default --silent`


## Too much clutter in command palette

If you don't want one of the build systems, you can just rename the `.sublime-build` extension to something else so that sublime doesn't recognize the file, or just delete the file.


## Builds

### Node

Simply runs a file with the `node ${file}`.

### ESM

Allows ES6 imports. Calls `node -r @std/esm ${file}`, which uses the version. This will only work if `@std/esm` is installed in the package directory.

### Babel

Executes a JS file but first pre-compiles it with babel. Calls `node -r ${packages}/BuildNode/node_modules/babel-cli/bin/babel-node.js ${file}`.

### Nvm Current

Executes a JS file with nvm run, which will use whatever version of node it finds in a `.nvmrc`. Calls `nvm run ${file}`. The instructions above must be followed for this to work properly, or else you'll get an error saying nvm isn't a command.

