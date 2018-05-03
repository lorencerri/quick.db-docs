# Quick.db

_This package is meant to provide an easy way to create and use a database, **all data is stored persistently**, and comes with a **queue system to prevent database locking.**_

_**Want to provide feedback or suggestions on Quick.db? **_[_**Click Here!**_](https://docs.google.com/forms/d/e/1FAIpQLSeggzYaYjg31bEmIkrKHEJ3-q-RC7KFxmmKQXs_c4tpnc5ctA/viewform?usp=send_form)

---

_**Note:** This package is under development and will be updated frequently._ **Current Version: 5.5.0**

**Installation**

```ruby
npm install quick.db
```

**Require Package**

```js
var db = require('quick.db')
```

[_v3.x/v4.x to v5.x Migration Guide_](https://github.com/Plexi-Development/quick.db/blob/quickdb/docs/MIGRATION.md)

#### View [Table Of Contents](/table-of-contents.md)

---

> #### External Links:
>
> > [**NPM Page**](https://www.npmjs.com/package/quick.db)**  /                          
> > **[**Discord**](https://discord.io/plexidev)**  /                          
> > **[**GitHub**](https://github.com/Plexi-Development/quick.db)

---

#### What is Quick.db?

> Quick.db is an easy to use database alternative, it was designed to be simple to let new users who are just getting into development not need  to worry about large-scale databases.
>
> It works by storing data to a set **ID**_\(key\)_, then access that persistent data anytime through a .fetch\(\) function.  
> You can think of it like putting data\(objects\) in boxes, then the label that box has on it being the **ID**. You can then find the box you are looking for just my pointing to its **ID**_\(label on the box\)_.

---

#### Example

> _All data in quick.db is stored **persistently** in a database. Here is an example of setting an object in the database, then fetching parts & the full object._

```js
const db = require('quick.db');

// Setting the FULL object
db.set('userInfo', { part1: 'Hello', part2: 'World!' }).then( i => console.log(i))
// -> { part1: 'Hello', part2: 'World!' }

// Fetching only PARTS of the object
db.fetch('userInfo', { target: '.part1' }).then( i => console.log(i)) // -> 'Hello'
db.fetch('userInfo', { target: '.part2' }).then( i => console.log(i)) // -> 'World!'

// Fetching the FULL object
db.fetch('userInfo').then( i => console.log(i))
// -> { part1: 'Hello', part2: 'World!' }
```

---

> #### Contributors
>
> > TrueXPixels  
> > Zelak312  
> > Morfixx  
> > ExtasyMonst4  
> > [_Plexi Development..._](https://discord.io/plexidev)



