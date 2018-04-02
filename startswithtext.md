### .startsWith\(text, _\[options\]_\) {#fetch}

> **Input**:  
>    text -&gt; string  
>    options -&gt; object
>
> **Returns: **Promise&lt;Array&gt;

```js
db.startsWith('userBalance').then(i => {
    console.log(i); 
    // Returns an array of every entry in the database where the ID starts with userBalance
    i.forEach(function(entry){
        console.log(entry);
        // Goes through each item in the response and console.logs it
    })
})
```

---

#### Options

> * **Parameter: **sort
> * **Type: **String
> * **Default: **_none  _
> * **Description: **Sorts the array by the object specified
> * **Example:**

```js
db.startsWith('userBalance', { sort: '.data'}).then(i => {
    console.log(i); 
    // Returns a SORTED array, where the beginning of the ID starts with 'userBalance'
})
```

#### Example Using "Sort"

![Imgur](https://i.imgur.com/glWkdWI.png)

