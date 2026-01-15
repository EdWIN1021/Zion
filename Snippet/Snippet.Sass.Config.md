# Config

Owner: Edwin

## Initialize project

```bash
npm install node-sass
```

## Create css file

```bash
mkdir css
touch css/style.css
```

## Create sass file

```bash
mkdir sass
touch sass/main.scss
```

## Add script to package.json

```json
"scripts": {
	"compile:sass": "node-sass sass/main.scss css/style.css -w"
}
```