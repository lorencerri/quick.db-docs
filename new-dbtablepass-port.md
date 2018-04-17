### new db.table\(name\) {#push}

> **Input:                    
>    **name -&gt; String
>
> **Returns: **Should be stored in a variable

```js
// Require Package
const db = require('quick.db');

// Create Table
const userInfo = new db.table('UserInfo');

/*
 The userInfo now works exactly the same as 'db'
 Although, now all data is separate from other tables
*/

// Setting Number - userInfo Table
userInfo.set('main', 5);

// Setting Number - Main Table
db.set('main', 1);

// Fetching Number - userInfo Table
userInfo.fetch('main').then(i => {
    console.log(i);
    // -> 5
})

// Fetching Number - Main Table
db.fetch('main').then(i => {
    console.log(i);
    // -> 1
})
```

---

#### **Example:**

_**You can view the output of this **_[_**here**_](https://quickdb-latest.glitch.me/data/?password=pass111)_** in the WebViewer.**_  
![Imgur](https://i.imgur.com/vpcp5Pj.png)

