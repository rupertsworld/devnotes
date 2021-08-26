# Get Base64 string from image URL (Node)

```js
var request = require('request').defaults({ encoding: null });

function getBase64(url) {
	return new Promise((resolve, reject) => {
		request.get(url, function (error, response, body) {
			if (!error && response.statusCode == 200) {
				data = "data:" + response.headers["content-type"] + ";base64," + Buffer.from(body).toString('base64');
				resolve(data);
			} else {
				reject();
			}
		});
	});
}

```