# Flash-Of-Unstyled-Content

Sometimes, in your website you will hit an issue, which your styles will load after your dom and your content loads, and this cause an unwanted flash of your content which is really bad.

## Solution

first, take a look at this => `dom readyState` and understand what it is: `https://developer.mozilla.org/en-US/docs/Web/API/Document/readyState`

To solve our problem, we will use `dom readyState` feature.

I found the solution from this link: `https://medium.com/@fbnlsr/how-to-get-rid-of-the-flash-of-unstyled-content-d6b79bf5d75f`

first make your body visibility hidden:

```js
<body style="visibility: hidden;">
  <!-- Your awesome website -->
</body>
```

then when your dom has loaded is ready call this function inside `useEffect` of your react application to make your body visible again.

```js
useEffect(() => {
  // Helper function
  let domReady = (cb) => {
    document.readyState === 'interactive' || document.readyState === 'complete'
      ? cb()
      : document.addEventListener('DOMContentLoaded', cb);
  };

  domReady(() => {
    // Display body when DOM is loaded
    document.body.style.visibility = 'visible';
  });
}, [])
```

That's it 

Enjoy it :))
