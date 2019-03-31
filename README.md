Reproduction steps:

1.  `yarn init` (use all default settings)
2.  `yarn add -D nyc@13.3.0 --exact`
3.  Create `test.js` (can be empty)
4.  Add to `package.json`: `"scripts": { "test": "nyc node --experimental-worker test.js" }`

Expected behavior: `yarn test` succeeds.

Observed behavior: `yarn test` forks many instances of Node before crashing. `npm test` works as expected.

```
yarn run v1.15.2
$ nyc node --experimental-worker test.js
The syntax of the command is incorrect.
----------|----------|----------|----------|----------|-------------------|
File      |  % Stmts | % Branch |  % Funcs |  % Lines | Uncovered Line #s |
----------|----------|----------|----------|----------|-------------------|
All files |        0 |        0 |        0 |        0 |                   |
----------|----------|----------|----------|----------|-------------------|
error Command failed with exit code 255.
info Visit https://yarnpkg.com/en/docs/cli/run for documentation about this command.
```
