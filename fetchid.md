### .fetch\(ID, _\[options\]_\) {#fetch}

> **Input:              
>    **ID -&gt; String  
>    _options -&gt; Object **\(optional\)**_
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

#### Options

> * **Parameter: **target
> * **Type: **String
> * **Default: **_none  _
> * **Description: **Fetches the data from the target instead of the entire object.
> * **Example:**

```js
let data = { username: 'TrueXPixels', discrim: '0001' };
db.set('uniqueID', data).then(i => {
    console.log(i); // { username: 'TrueXPixels', discrim: '0001' }
})

db.fetch('uniqueID', { target: '.discrim' }).then(i => {
    console.log(i); // '0001'
})
```



