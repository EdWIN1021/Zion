### defer

```jsx
<script src="script.js" defer></script>
```

- When you include a script with the defer attribute, it tells the browser to download the script in the background while parsing the HTML document. However, the script execution is deferred until after the HTML document has been completely parsed.

### async

```jsx
<script src="script.js" async></script>
```

- When you include a script with the async attribute, it also tells the browser to download the script in the background. However, the key difference is that the script will be executed as soon as it's downloaded, regardless of whether the HTML parsing is complete or not.