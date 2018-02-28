### Storing Item Arrays & Fetching It {#example2}

_This example stores items in an array, then fetches it later on._

---

```js
// Require Package
const db = require('quick.db');

// Create & Push stone object
let stone = { name: 'Stone', ID: 1, description: 'An impassable grey solid object.', icon: 'icons/stone.png' };
db.push('items', stone); // Push the item into the 'items' array in the database

// Create & Push wood object
let wood = { name: 'Wood', ID: 2, description: 'Great for floors!', icon: 'icons/wood.png' };
db.push('items', wood); // Push the item into the 'items' array in the database

// Fetch Items
db.fetch('items').then(i => { // Fetch the items array from the database
    console.log(typeof i); // 'object' 
    console.log(i); 
    /* [ { name: 'Wood', ID: 2, description: 'Great for floors!', icon: 'icons/wood.png' }, 
        { name: 'Stone', ID: 1, description: 'An impassable grey solid object.', icon: 'icons/stone.png' } ] */
    console.log(i[0].name) // 'Wood'

    // Loops
    for (var obj in i) {
        console.log(obj[i]); // Returns every object in the array [1]
    }

    for (var obj in i) {
        console.log(obj[i].name); // Returns every object name in the array [2]
    }

})
```

###### \[1\]

```js
{ name: 'Wood', ID: 2, description: 'Great for floors!', icon: 'icons/wood.png' }
{ name: 'Stone', ID: 1, description: 'An impassable grey solid object.', icon: 'icons/stone.png' }
```

###### \[2\]

```js
'Wood'
'Stone'
```



