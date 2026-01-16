- v-html会先移除节点下的所有节点，调用html方法，通过addProp添加innerHTML属性，归根结底还是设置innerHTML为v-html的值

> 💡output real HTML
> 

```
data() {
  return { rawHtml: "<h2>Hello World</h2>" };
},

<div v-html="rawHtml"></div>

```