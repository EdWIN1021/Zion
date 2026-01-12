```json
{
  "compilerOptions": {
    /* Base Options: */
    "esModuleInterop": true,
    "skipLibCheck": true,
    "target": "es2022",
    "allowJs": true,
    "resolveJsonModule": true,
    "moduleDetection": "force",
    "isolatedModules": true,

    /* Strictness */
    "strict": true,
    "noUncheckedIndexedAccess": true,

    /* If transpiling with TypeScript: */
    "moduleResolution": "NodeNext",
    "module": "NodeNext",
    "outDir": "dist",
    "sourceMap": true,

    /* AND if you're building for a library: */
    "declaration": true,

    /* AND if you're building for a library in a monorepo: */
    "composite": true,
    "declarationMap": true,

    /* If NOT transpiling with TypeScript: */
    "moduleResolution": "Bundler",
    "module": "ESNext",
    "noEmit": true,

    /* If your code runs in the DOM: */
    "lib": ["es2022", "dom", "dom.iterable"],

    /* If your code doesn't run in the DOM: */
    "lib": ["es2022"]
  }
}
```




```
npx tsc --init

tsc // complie all ts files to js

---

## exclude

```json
// This property helps you control which files or directories should not be included when TypeScript compiles your code.
{
  "compilerOptions": {

  },
  "exclude": ["[file_name].ts", "node_modules"]
}
```


## include

```json
// This property helps you control which files TypeScript should compile and consider when processing your code.
{
  "compilerOptions": {

  },
  "include": ["[file_name].ts"]
}
```

---

## files

```json
// The "files" property is typically used when you want precise control over which individual files should be compiled
{
  "compilerOptions": {

	},
  "files": ["[file_name].ts"]
}
```

---

## target

```json

{
  "compilerOptions": {
		"target": "ES6",
  },
}
```

---

## outDir

```json
{
  "compilerOptions": {
		"outDir": "./dist",
  },
}
```

---

## rootDir

```json
{
  "compilerOptions": {
		"rootDir": "./src",
  },
}
```

---

## removeComments

```json
//remove all the comments in js files
{
  "compilerOptions": {
		"removeComments": true,
  },
}
```