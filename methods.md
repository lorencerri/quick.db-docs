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

### .fetch\(ID\) {#fetch}

> **Input:  
>    **_none_
>
> **Returns: **Promise&lt;data&gt;

```js
let data = { username: 'TrueXPixels', balance: 100 };
db.set('uniqueID', data);

db.fetch('uniqueID').then(i => {
    console.log(typeof i); // 'object'
    console.log(i); // { username: 'TrueXPixels', balance: 100 }
    console.log(i.username); // 'TrueXPixels'
})
```

---



