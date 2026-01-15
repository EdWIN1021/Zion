# clear float

Owner: Edwin

<aside>
💡 当所有子元素浮动的时候，且父元素没有设置高度时，这时父元素就会产生高度塌陷

</aside>

```css
@mixin clearfix {
  &::after {
    content: "";
    display: block;
    clear: both;
  }
}
```