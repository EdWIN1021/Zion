# @mixin

Owner: Edwin

<aside>
💡 encapsulating reusable styles within blocks.

</aside>

## Sass Input

```css
@mixin button-styles($color) {
	padding: 10px;
	background-color: blue;
	color: $color;
}

.primary-button {
	@include button-styles(white);
}
```

## Css Output

```css
.primary-button {
	padding: 10px;
	background-color: blue;
	color: white;
}
```