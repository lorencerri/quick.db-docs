### Storing, Updating & Fetching A Number - _Beginner_ {#example1}

_This example takes a starting number, then changes it a bit, and finally fetches it later on._

---

```js
// Require Package, we always need to do this when using packages.
const db = require('quick.db');

// Define Starting Value
db.set('userBalance', 0); // This sets the number 0, to the ID: 'userBalance', so it can be fetched using the ID later on.
// When using numbers, you can just .add() or .subtract(), no need to define it as 0 first

// Log Current Balance - When fetching, we supply it an ID to direct to the associated data.
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



