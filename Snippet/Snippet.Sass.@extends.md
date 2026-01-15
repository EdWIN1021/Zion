# @extends

Owner: Edwin

<aside>
💡 sharing common styles among selectors

</aside>

## Sass Input

```css
%button-base {
	padding: 10px;
	background-color: blue;
	color: white;
}

.primary-button {
	@extend %button-base;
}

```

## Css output

```css
.primary-button, %button-base {
	padding: 10px;
	background-color: blue;
	color: white;
}

```