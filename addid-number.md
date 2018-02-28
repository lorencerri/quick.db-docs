### .add\(ID, number, _\[options\]_\) {#add}

> **Input:                                        
>    **ID -&gt; String  
>    number -&gt; Number  
>    _options -&gt; Object **\(optional\)**_
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

#### Options

> * **Parameter: **target
> * **Type: **String
> * **Default: **_none  _
> * **Description: **Adds to the number in the target instead of the entire object.
> * **Example:**

```js
let data = { username: 'TrueXPixels', balance: 100 };
db.set('uniqueID', data).then(i => {
    console.log(i); // { username: 'TrueXPixels', balance: 100 }
})

db.add('uniqueID', 50, { target: '.balance' }).then(i => {
    console.log(i); // 150
})
```



