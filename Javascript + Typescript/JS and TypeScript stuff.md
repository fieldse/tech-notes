
### Generate array from range N, do some function

For N items, do some function and return the results as an array.

```js

const someFunc = () => 'foo';
const n = 20

const results = [Array(n).map((_) => someFunc()]
```


### Running typescript files with `import` from console

credit: https://bobbyhadz.com/blog/typescript-cannot-use-import-statement-outside-module

Running typescript files directly from the console is tricky.
1. You can't run them directly with just `node somescript.ts`
2. Files with imports will fail, unless you configure `ts-config.json` correctly.

Solution:
1. Install `ts-node`
2. Change the `module` line in your `ts-config.json` compiler options to `common-js`:

```json
  "compilerOptions": {
    "target": "es6",
    "module": "commonjs",
    ...
```

3. Run the command first in the console to test it, specifying the `ts-config.json` config file:
```
npx ts-node --project ./tsconfig.json script/seed-database 
```

4. If everything works, add the line to your `package.json` under `scripts`:

```json
"scripts": {
"db:seed": "ts-node --project ./tsconfig.json script/seed-database",
...
},
```