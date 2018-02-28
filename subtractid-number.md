### .subtract\(ID, number\) {#subtract}

> **Input:                                          
>    **ID -&gt; String  
>    number -&gt; Number
>
> **Returns: **Promise&lt;updatedObject&gt;

```js
let startingNumber = 100;

// Sets the initial number into the object
db.set('uniqueID', startingNumber);

// Subtracts 25 to the existing number @ ID: 'uniqueID'
db.subtract('uniqueID', 25).then(i => console.log(i)); // 75

// Subtracts 50 to the existing number @ ID: 'uniqueID'
db.subtract('uniqueID', 50).then(i => console.log(i)); // 25

// Fetches object @ ID: 'uniqueID'
db.fetch('uniqueID').then(i => {
    console.log(typeof i); // 'number'
    console.log(i); // 150
})
```

---

#### Options

> * **Parameter: **target
> * **Type: **String
> * **Default: **_none  _
> * **Description: **Subtracts from the number in the target instead of the entire object.
> * **Example:**

```js
let data = { username: 'TrueXPixels', balance: 100 };
db.set('uniqueID', data).then(i => {
    console.log(i); // { username: 'TrueXPixels', balance: 100 }
})

db.subtract('uniqueID', 50, { target: '.balance' }).then(i => {
    console.log(i); // 50
})
```



