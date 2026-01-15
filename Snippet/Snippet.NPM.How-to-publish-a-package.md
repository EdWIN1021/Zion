### Step1

- modify package.json

```json
"name": "@<organization-name>/<package-name>"
```

### Step2

- publish to npm

```shell
npm publish --access public
```

---

### Update Package

- increment version number

```shell
npm version patch
```

- push to npm 

```shell
npm publish
```