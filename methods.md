### .set\(ID, data,_ \[options\]_\) {#set}

> **Input:                  
>    **ID -&gt; String  
>    data -&gt; Any \(obj, array, number, string, etc.  
>    _options -&gt; Object **\(optional\)**_  
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

#### Options

> * **Parameter: **target
> * **Type: **String
> * **Default: **_none  _
> * **Description: **Sets the data to the target instead of the entire object.
> * **Example:**

```js
let data = { username: 'TrueXPixels', discrim: '0001' };
db.set('uniqueID', data).then(i => {
    console.log(i); // { username: 'TrueXPixels', discrim: '0001' }
})

// Sets uniqueID.discrim to 9999, instead of uniqueID to 9999
db.set('uniqueID', '9999', { target: '.discrim' });

db.fetch('uniqueID').then(i => {
    console.log(i); //{ username: 'TrueXPixels', discrim: '9999' }
    console.log(i.discrim); // '9999'
})
```



