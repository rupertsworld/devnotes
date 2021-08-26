- [Basics of writing an add-on](https://www.labnol.org/internet/write-google-docs-addon/28446/) – and the [official guide](https://developers.google.com/workspace/add-ons/editors/sheets)
- [Clasp for local editing](https://github.com/google/clasp#push)
- [Dialogs & sidebar add-ons](https://developers.google.com/workspace/add-ons/concepts/dialogs)
- [UI creation functions](https://developers.google.com/apps-script/reference/base/ui#createAddonMenu())
- [How to publish an add-on](https://developers.google.com/workspace/add-ons/how-tos/publish-add-on-overview) (we do this at the end)

## Basic setup for a sidebar app

Showing the sidebar:

```js
function showSidebar() {
  const html = 
     HtmlService.createTemplateFromFile("sidebar")
    	.evaluate()
    	.setTitle("Sheets For Humans");
  SpreadsheetApp.getUi().showSidebar(html);
}
```

Adding the menu item to show the sidebar:

```js
function onInstall() {
  onOpen();
}

function onOpen() {
  DocumentApp.getUi()
    .createAddonMenu()
    .addItem("Sheets For Humans", "showSidebar")
    .addToUi();
}
```

Connecting from sidebar UI to Apps Script functions:

```js
document.querySelector('#button')
  .addEventListener('click', () => {
     google.script.run.myFunctionName();
	});
```

Transcluding separated JS/CSS code:

```
<?!= include('myJavascriptFile'); ?>
```

Where we have the function include:

```js
function include(filename) {
  return HtmlService.createHtmlOutputFromFile(filename)
      .getContent();
}
```



with filename `myJavascriptFile.html`



## Google Sheets

- Research on getting cell values: [1](https://blog.gsmart.in/google-sheet-script-get-cell-value/) [2](https://developers.google.com/apps-script/guides/sheets)
- The "[Range](https://developers.google.com/apps-script/reference/spreadsheet/range)" class

