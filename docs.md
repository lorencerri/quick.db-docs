### Documentation {#table}

##### Methods

* [new db.table\(name\)](/new-dbtablepass-port.md)
* [.add\(key, number, \[options\]\) -&gt; updatedRow](#add-method)
* [.all\(\) -&gt; array](#all-method)
* [.delete\(key, \[options\]\) -&gt; boolean](#delete)
* [.get\(key, \[options\]\) -&gt; row](#get)
* [.has\(key, \[options\]\) -&gt; boolean](#has)
* [.push\(key, element, \[options\]\) -&gt; updatedRow](#push)
* [.set\(key, data, \[options\]\) -&gt; updatedRow](#set-method)
* [.subtract\(key, number, \[options\]\) -&gt; updatedRow](#subtract)
* [.startsWith\(str, \[options\]\) -&gt; array](#starts-with)

---

##### **new .table\(**_**name**_**\)** {#table}

This function creates a new table, allowing you to separate your data while being used exactly the same.

```js
var economy = new db.table('economy')
economy.set('myBalance', 500) // -> 500
economy.get('myBalance') // -> 500
db.get('myBalance') // -> null
```

---

##### .add\(_key_, _number, \[options\]_\) -&gt; updatedRow {#add-method}

This function adds a number to a key in the database. \(If no existing number, it will add to 0\)

```js
db.get('myBalance')
// -> 500

db.add('myBalance', 250)
// -> 750
```

_Also allows for accessing properties using dot notation_

```js
db.get('myUser')
// -> { guild: null, balance: 500 }

db.add('myUser.balance', 250)
// -> { guild: null, balance: 750 }
```

---

##### **.all\(\) -&gt; array** {#all-method}

This function returns the entire active table as an array.

```js
db.all()
// -> [Array]
```

---

##### **.delete\(**_**key**_**, **_**\[options\]**_**\) -&gt; boolean** {#delete}

This function deletes the specified key. Returns if it was a success or not.

```js
db.get('myData')
// -> "Hello World!"

db.delete('myData')
// true
```

_Also allows for accessing properties using dot notation_

```js
db.get('myUser')
// -> { guild: null, balance: 500 }

db.delete('myUser.balance')
// -> true

db.get('myUser')
// -> { guild: null }
```

---

##### **.get\(**_**key**_**, **_**\[options\]**_**\) -&gt; row** {#get}

This function returns data from a row based on the key. **Alias: .fetch\(\)**

```js
db.set('myData', 'Hello World!')
// -> 'Hello World!'

db.get('myData')
// -> 'Hello World!'
```

_Also allows for accessing properties using dot notation_

```js
db.set('myUser', { guild: 'Plexi', balance: 500 })
// -> { guild: 'Plexi', balance: 500 }

db.get('myUser.guild') // -> "Plexi"
db.get('myUser.balance') // -> 500
db.get('myUser.notAProp') // -> undefined
```

---

##### **.has\(**_**key**_**,**_** \[options\]**_**\) -&gt; boolean** {#has}

This function returns a boolean based on whether an element or property exists. **Alias: .exists\(\)**

```js
db.set('myData', 'Hello World!')
// -> 'Hello World!'

db.has('myData') // -> true
```

_Also allows for accessing properties using dot notation_

```js
db.set('myUser', { guild: 'Plexi', balance: 500 })
// -> { guild: 'Plexi', balance: 500 }

db.has('myUser.guild') // -> true
db.has('myUser.items') // false
```

---

##### **.push\(**_**key**_**, **_**element**_**, **_**\[options\]**_**\) -&gt; updatedRow** {#push}

This function will push into an array in the database based on the key. \(If no existing array, it will create one\)

```js
db.set('myItems', ['Sword', 'Lock'])
// -> ['Sword', 'Lock']

db.push('myItems', 'Dagger')
// -> ['Sword', 'Lock', 'Dagger']
```

_Also allows for accessing properties using dot notation_

```js
db.set('myUser', { balance: 500, items: ['Watch', 'Sword'] })
// -> { balance: 500, items: ['Watch', 'Sword'] }

db.push('myUser.items', 'Dagger')
// -> { balance: 500, items: ['Watch', 'Sword', 'Dagger'] }
```

---

##### **.set\(**_**key**_**, **_**data**_**, **_**\[options\]**_**\) -&gt; updatedRow** {#set-method}

This function sets new data based on a key in the database. \(When using dot notation, if the object doesn't exist it'll create one\)

```js
db.set('myData', 'Hello World!') // -> 'Hello World!'
db.set('myData', 50) // -> 50
db.set('myData', { foo: 'bar' }) // -> { foo: 'bar' }
```

_Also allows for accessing properties using dot notation_

```js
db.get('myUser') // -> null

db.set('myUser.guild.rank', 'Mage') 
// -> { guild: { rank: 'Mage' } }

db.set('myUser.balance', 500) 
// -> { guild: { rank: 'Mage' }, balance: 500 }

db.set('myUser.guild.rank', 'Warrior') 
// -> { guild: { rank: 'Warrior' }, balance: 500 }
```

---

##### **.startsWith\(**_**str**_**, **_**\[options\]**_**\) -&gt; array** {#starts-with}

This function fetches everything that starts with a certain string. Allows you to sort the data as well.

```js
/* In this example, assume the data is stored as follows:
{ ID: 'userInfo_1', data: { username: 'User', balance: 9000 } }
{ ID: 'userInfo_2', data: { username: 'User1', balance: 500 } }
{ ID: 'userInfo_3', data: { username: 'User2', balance: 10 } }
{ ID: 'userInfo_4', data: { username: 'User3', balance: 4000 } }
{ ID: 'userInfo_5', data: { username: 'User4', balance: 300 } }
{ ID: 'userInfo_6', data: { username: 'User5', balance: 50 } }
{ ID: 'userInfo_7', data: { username: 'User6', balance: 9999 } }
{ ID: 'userInfo_8', data: { username: 'User7', balance: 700 } }
*/

// NOTE: Sorting is optional.
db.startsWith('userBalance', { sort: true, sortBy: '.balance' });
/* Output:
[ { ID: 'userInfo_7', data: { username: 'User6', balance: 9999 } },
{ ID: 'userInfo_1', data: { username: 'User', balance: 9000 } },
{ ID: 'userInfo_4', data: { username: 'User3', balance: 4000 } },
{ ID: 'userInfo_8', data: { username: 'User7', balance: 700 } },
{ ID: 'userInfo_2', data: { username: 'User1', balance: 500 } },
{ ID: 'userInfo_5', data: { username: 'User4', balance: 300 } },
{ ID: 'userInfo_6', data: { username: 'User5', balance: 50 } },
{ ID: 'userInfo_3', data: { username: 'User2', balance: 10 } } ]
*/
```

*Another example if the data is not an object*
```js
/* In this example, assume the data is stored as follows:
{ ID: 'userBalance_1', data: 9000 },
{ ID: 'userBalance_2', data: 500 },
{ ID: 'userBalance_3', data: 10 },
{ ID: 'userBalance_4', data: 4000 },
{ ID: 'userBalance_5', data: 300 },
{ ID: 'userBalance_6', data: 50 },
{ ID: 'userBalance_7', data: 10000 },
{ ID: 'userBalance_8', data: 700 }
*/

// NOTE: Sorting is optional.
db.startsWith('userBalance', { sort: true });
/* Output:
[ { ID: 'userBalance_7', data: 10000 },
{ ID: 'userBalance_1', data: 9000 },
{ ID: 'userBalance_4', data: 4000 },
{ ID: 'userBalance_8', data: 700 },
{ ID: 'userBalance_2', data: 500 },
{ ID: 'userBalance_5', data: 300 },
{ ID: 'userBalance_6', data: 50 },
{ ID: 'userBalance_3', data: 10 } ]
*/

```

---

##### **.subtract\(**_**key**_**,**_** number**_**, **_**\[option\]**_**\) -&gt; updatedRow** {#subtract}

This function subtracts a number to a key in the database. \(If no existing number, it will subtract from 0\)

```js
db.get('myBalance') // -> 500
db.subtract('myBalance', 200) // -> 300
```

_Also allows for accessing properties using dot notation_

```js
db.get('myUser', { league: 'Gold', XP: 500 }) // -> { league: 'Gold', XP: 500 }
db.subtract('myUser.XP', 200) // -> { league: 'Gold', XP: 300 }
```

---



