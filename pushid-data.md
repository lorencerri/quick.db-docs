### .push\(ID, data\) {#set}

> **Input:            
>    **ID -&gt; String  
>    data -&gt; Any \(obj, array, number, string, etc.\)
>
> **Returns: **Promise&lt;updatedData&gt;

_Target has to be an array._

```js
let ids = [100, 40, 500, 20];

// Set the array to the ids @ ID: 'uniqueID'
db.set('uniqueID', ids).then(i => {
    console.log(typeof i) // 'object'
    console.log(i); // [100, 40, 500, 20]
    console.log(i[0]); // 100
})

db.push('uniqueID', 10).then(i => console.log(i)); // [100, 40, 500, 20, 10]
db.push('uniqueID', 'Hello World!').then(i => console.log(i)); // [100, 40, 500, 20, 10, 'Hello World!']

db.fetch('uniqueID').then(i => {
    console.log(typeof i); // 'object'
    console.log(i); // [100, 40, 500, 20, 10, 'Hello World!']
    console.log(i[0]); // 100
})

```

---



