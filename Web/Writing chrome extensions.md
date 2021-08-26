# Handy stuff

### Getting current tab URL

```js
async function getCurrentTabURL() {
  return new Promise((resolve) => {
    chrome.tabs.query({ currentWindow: true, active: true }, (tabs) => {
      resolve(tabs[0].url)
    })
  })
}
```