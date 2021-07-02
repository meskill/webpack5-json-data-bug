# Webpack bug

The bug will crash webpack watching mode with error `TypeError: Cannot read property 'jsonData' of undefined`

## Steps to reproduce

1. Clone this repo
2. Install dependencies `npm ci`
3. Run webpack watch mode `npm start`
4. Make some changes to `./src/index.js` and save it to trigger rebuild
5. After second save webpack will crash with following error:
    ```
    TypeError: Cannot read property 'jsonData' of undefined
        at JsonGenerator.getSize (/workspaces/js-ts/webpack5-json-data-bug/node_modules/webpack/lib/json/JsonGenerator.js:119:31)
        at NormalModule.size (/workspaces/js-ts/webpack5-json-data-bug/node_modules/webpack/lib/NormalModule.js:1224:43)
        at NormalModule.cleanupForCache (/workspaces/js-ts/webpack5-json-data-bug/node_modules/webpack/lib/NormalModule.js:364:9)
        at NormalModuleFactory.cleanupForCache (/workspaces/js-ts/webpack5-json-data-bug/node_modules/webpack/lib/NormalModuleFactory.js:670:11)
        at Compiler._cleanupLastNormalModuleFactory (/workspaces/js-ts/webpack5-json-data-bug/node_modules/webpack/lib/Compiler.js:383:34)
        at Compiler.createNormalModuleFactory (/workspaces/js-ts/webpack5-json-data-bug/node_modules/webpack/lib/Compiler.js:1049:8)
        at Compiler.newCompilationParams (/workspaces/js-ts/webpack5-json-data-bug/node_modules/webpack/lib/Compiler.js:1071:30)
        at Compiler.compile (/workspaces/js-ts/webpack5-json-data-bug/node_modules/webpack/lib/Compiler.js:1082:23)
        at /workspaces/js-ts/webpack5-json-data-bug/node_modules/webpack/lib/Watching.js:188:19
        at Hook.eval [as callAsync] (eval at create (/workspaces/js-ts/webpack5-json-data-bug/node_modules/tapable/lib/HookCodeFactory.js:33:10), <anonymous>:15:1)
    ```