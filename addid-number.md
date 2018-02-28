### .add\(ID, number\) {#delete}

> **Input:                                  
>    **ID -&gt; String  
>    number -&gt; Number
>
> **Returns: **Promise&lt;updatedObject&gt;

```js
let startingNumber = 0;

// Sets the initial number into the object
db.set('uniqueID', startingNumber);

// Adds 50 to the existing number @ ID: 'uniqueID'
db.add('uniqueID', 50).then(i => console.log(i)); // 50

// Adds 100 to the existing number @ ID: 'uniqueID'
db.add('uniqueID', 100).then(i => console.log(i)); // 150

// Fetches object @ ID: 'uniqueID'
db.fetch('uniqueID').then(i => {
    console.log(typeof i); // 'number'
    console.log(i); // 150
});
```

---



