### Storing, Updating & Fetching A Number

_This example takes a starting number, then changes it a bit, and finally fetches it later on._

---

```js
// Require Package
const db = require('quick.db');

// Define Starting Value
db.set('userBalance', 0); // When using numbers, you can just .add() or .subtract(), no need to define it as 0 first

// Log Current Balance
db.fetch('userBalance').then(i => console.log(i, typeof i)); // 0 'number'

// Add 100 to ID: userBalance - Remember, .add() also returns the updated object
db.add('userBalance', 100).then(i => console.log(i, typeof i)); // 100 'number'

// Subtract 25 from ID: userBalance - Remember, .subtract() also returns the updated object
db.subtract('userBalance', 25).then(i => console.log(i, typeof i)); // 75 'number'

// Fetch Final Number
db.fetch('userBalance').then(i => {
    console.log(typeof i); // 'number'
    console.log(i); // 75
})
```



