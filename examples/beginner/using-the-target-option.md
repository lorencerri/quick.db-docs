### Using The { target } Option

_This example will go over using the **{ target } **option in the functions._

---

```js
// Require Package
const db = require('quick.db');

// Set Database
db.set('userData', { username: 'TrueXPixels', balance: 100, discrim: '0001' })

// You can use the fetch option to get specific items in an object
db.fetch('userData', { target: '.discrim' }).then(i => {
    console.log(i); // '0001'
})

// You can also set specific items in an object, instead of the entire object
db.set('userData', '9999', { target: '.discrim' }).then(i => {
// Instead of setting 'userData' to 9999, it set userData.discrim to 9999
    console.log(i); // { username: 'TrueXPixels', balance: 100, discrim: '9999' }
})

// You can also add to specific items in an object, instead of the entire object
db.add('userData', 50, { target: '.balance' }).then(i => {
    console.log(i) // { username: 'TrueXPixels', balance: 150, discrim: '9999' }
})

// You can also subtract from specific items in an object, instead of the entire object
db.subtract('userData', 25, { target: '.balance' }).then(i => {
    console.log(i) // { username: 'TrueXPixels', balance: 125, discrim: '9999' }
})

// Now, we can fetch only the balance using what we just learned
db.fetch('userData', { target: '.balance' }).then(i => {
    console.log(i); // 125
})

// NOTE: target also supports nested objects! Example:
let guildObj = {
    owner: {
        username: 'TrueXPixels',
        discrim: '0001'
    },
    primaryChannel: {
        name: 'General',
        members: 500
        pastNames: [
            'Testing',
            'Bots',
            'Bot-Invite',
            'Chat'
        ]
    }
}

// Set Database
db.set('guild', guildObj)

// This is an example of fetching past names
db.fetch('guild', { target: '.primaryChannel.pastNames' }).then(i => {
    console.log(i); // ['Testing', 'Bots', 'Bot-Invite', 'Chat']
})

// Here's an example of setting the discrim of the owner
db.set('guild', '9999', { target: '.owner.discrim' })

// This is an example of fetching the owners discrim
db.fetch('guild', { target: '.owner.discrim' }).then(i => {
    console.log(i); // '0001'
})

// We can also add 100 to primaryChannel.members
db.add('guild', 100, { target: '.primaryChannel.members' }).then(i => {
    console.log(i); // [1]
})
```

---

###### \[1\]

```
owner: {
    username: 'TrueXPixels',
    discrim: '0001'
},
primaryChannel: {
    name: 'General',
    members: 600
    pastNames: [
        'Testing',
        'Bots',
        'Bot-Invite',
        'Chat'
    ]
}
```



