```js
const express = require('express');
const app = express();
const cors = require('cors');
const port = 3000 | process.env.port;

app.use(express.json());


/*
// yarn add cors THEN
app.use(cors());
// OR
app.use(cors({
  origin: 'http://yourapp.com'
}));
*/

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example app listening at ${port}`)
})
```

