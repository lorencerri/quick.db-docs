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



