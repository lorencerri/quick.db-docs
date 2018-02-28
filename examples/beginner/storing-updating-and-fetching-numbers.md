### Storing, Updating & Fetching A Number - _Beginner_ {#example1}

_This example takes a starting number, then changes it a bit, and finally fetches it later on._

---

```js
// Require Package, we always need to do this when using packages
const db = require('quick.db');

// Define Starting Value
db.set('userBalance', 0); // This sets the number 0, to the ID: 'userBalance', so it can be fetched using the ID later on
// When using numbers, you can just .add() or .subtract(), no need to define it as 0 first

// Log Current Balance - When fetching, we supply it an ID to direct to the associated data
db.fetch('userBalance').then(i => console.log(i, typeof i)); // 0 'number'

// Adds 100 to the existing number @ ID: 'userBalance' [Which is currently 0]
// Remember, .add() also returns the updated object
db.add('userBalance', 100).then(i => console.log(i, typeof i)); // 100 'number'

// Subtracts 25 to the existing number @ ID: 'userBalance' [Which is currently 100]
// Remember, .subtract() also returns the updated object
db.subtract('userBalance', 25).then(i => console.log(i, typeof i)); // 75 'number'

// Fetches object @ ID: 'userBalance'
db.fetch('userBalance').then(i => { // Fetches the data @ the ID: 'userBalance'
    console.log(typeof i); // 'number'
    console.log(i); // 75
})
```



