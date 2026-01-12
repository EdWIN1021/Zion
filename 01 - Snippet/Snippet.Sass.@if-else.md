# @if-else

Owner: Edwin

```sass
@mixin fontColor($color) {
	@if $color == blue {
		color:blue;
	}
	@else {
		color:red;
	}
}

.box1 {
	@include fontColor(blue)
}

.box2 {
	@include fontColor(red)
}

```