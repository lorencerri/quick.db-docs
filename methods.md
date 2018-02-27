### .set\(ID, data\) {#set}

> **Input:          
>    **ID -&gt; String  
>    data -&gt; Any \(obj, array, number, string, etc.\)
>
> **Returns: **Promise&lt;updatedData&gt;

```js
let data = { username: 'TrueXPixels', balance: 100 };
db.set('uniqueID', data).then(i => {
    console.log(typeof i) // 'object'
    console.log(i); // { username: 'TrueXPixels', balance: 100 }
    console.log(i.username); // 'TrueXPixels'
})
```

---



