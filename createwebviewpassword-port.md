### .createWebview\(password, port\) {#push}

> **Input:                
>    **password -&gt; String  
>    port -&gt; Number, **or** _`process.env.PORT`_
>
> **Returns: **Console log of active port

```js
// Require Package
const db = require('quick.db');

// Create Webview
db.createWebview('password', process.env.PORT); // process.env.PORT creates the webview on the default port

// Output Below
// Usually @ localhost:PORT

// Glitch: Press "Show"
// AWS Cloud9: Press "Preview"
```

---

#### **Output:**

| Image | Description |
| --- | --- |
| ![Imgur](https://i.imgur.com/FXyDBdL.png) | Login Page| 
| ![Imgur](https://i.imgur.com/fIMIMWI.png) | Data View |

