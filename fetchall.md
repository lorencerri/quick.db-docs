### .fetchAll\(\) {#fetch}

> **Input**:  
>    _None_
>
> **Returns: **Promise&lt;Array&gt;

```js
db.fetchAll().then(i => {
    console.log(i); 
    // Returns an array of every entry in the database
    i.forEach(function(entry){
        console.log(entry);
        // Goes through each item in the response and console.logs it
    })
})
```

---



