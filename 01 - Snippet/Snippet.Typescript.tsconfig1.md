# tsconfig

Owner: Edwin

```bash
npx tsc --init

tsc // complie all ts files to js
```

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

---

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