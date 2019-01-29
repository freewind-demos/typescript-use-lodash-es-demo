TypeScript Use Lodash-ES Demo
=============================

Use `lodash-es` in typescript, but have errors.

```
npm install
npm run demo
```

It reports error:

```
/Users/freewind/workspace/typescript-use-lodash-es-demo/node_modules/lodash-es/upperCase.js:1
(function (exports, require, module, __filename, __dirname) { import createCompounder from './_createCompounder.js';
                                                                     ^^^^^^^^^^^^^^^^

SyntaxError: Unexpected identifier
    at new Script (vm.js:79:7)

```

The reason is, when we use typescript or `ts-node`,
it requires the code in packages are old plain JavaScript.

But the code in "lodash-es", which uses `import from` syntax:

```
import createCompounder from './_createCompounder.js';
```

Without the help from webpack, typescript will keep code in packages unchanged,
and node can't run them successfully without plugins.
