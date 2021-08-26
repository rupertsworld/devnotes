```js
await fetch('https://httpbin.org/post', {
    method: 'post',
  	body: JSON.stringify(body)
    headers: {
      'Accept': 'application/json',
      'Content-Type': 'application/json'
    }
  });
```

Note the 'no-cors' thing caused issue for me.

