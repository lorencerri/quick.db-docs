# Quick.db

_This package is meant to provide an easy way to create and use a database, **all data is stored persistently**, and comes with a **queue system to prevent database locking.**_

---

&lt;div align="center"&gt;

```
&lt;p&gt;

    &lt;a href="https://discord.io/plexidev"&gt;&lt;img src="https://discordapp.com/api/guilds/343572980351107077/embed.png" alt="Discord Server" /&gt;&lt;/a&gt;

    &lt;a href="http://www.youtube.com/subscription\_center?add\_user=TrueXPixels"&gt;&lt;img src="https://img.shields.io/badge/Subscribe-YouTube-red.svg" alt="YouTube Channel" /&gt;&lt;/a&gt;       

&lt;/p&gt;
```

&lt;/div&gt;

\*\*Note:\*\* This package is under development and will be updated frequently.

This package is meant to provide an easy way to create and use a database, \*\*all data is stored persistently\*\*, and comes with a \*\*queue system to prevent database locking\*\*.

---

\*\*Installation\*\*

\`\`\`

npm install quick.db

\`\`\`

\*\*Require Package\*\*

\`\`\`

var db = require\('quick.db'\)

\`\`\`

\*\[v3.x/v4.x to v5.x Migration Guide\]\([https://github.com/TrueXPixels/quick.db/blob/master/MIGRATION.md\)\*](https://github.com/TrueXPixels/quick.db/blob/master/MIGRATION.md%29*)

---

\#\# Table Of Contents

\*\*\[.set\(uniqueID, data\)\]\(\#set\)\*\* - \*Sets data to the uniqueID you supply, data can be anything: objects, arrays, strings, numbers, etc.\*

\*\*\[.fetch\(uniqueID\)\]\(\#fetch\)\*\* - \*Fetches the data using the uniqueID you assigned earlier\*

\*\*\[.delete\(uniqueID\)\]\(\#delete\)\*\* - \*Deletes an object using the uniqueID you assigned earlier\*

\*\*\[.push\(uniqueID, data\)\]\(\#push\)\*\* - \*Pushes a new item to an \_\_ARRAY\_\_, if target is not an array, it supplys a non-breaking error\*

\*\*\[.add\(uniqueID, number\)\]\(\#add\)\*\* - \*Adds the specified amount to a \_\_NUMBER\_\_, if target is not a number, it supplys a non-breaking error\*

\*\*\[.subtract\(uniqueID, number\)\]\(\#subtract\)\*\* - \*Subtracts the specified amount to a \_\_NUMBER\_\_, if target is not a number, it supplys a non-breaking error\*

\*\*\[Frequently Asked Questions\]\(\#FAQ\)\*\* - \*Some common questions, errors, etc.\*

\*\*\[Projects Using Quick.db\]\(\#projects\)\*\* - \*Lists a few projects that use quick.db\*

\#\# Documentation

&lt;a name="set"&gt;&lt;/a&gt;\*\*.set\(ID, data\)\*\* - \*Assigns the given data to the given ID\*

\*&gt; Optionally returns the set data\*

\`\`\`js

db.set\('uniqueID', { username: 'TrueXPixels', money: 400 }\).then\(i =&gt; {

console.log\(typeof i\) // object

console.log\(i\) // { username: 'TrueXPixels', money: 400 }

console.log\(i.money\) // 400

}\)

db.set\('uniqueID', 'Hello World!'\).then\(i =&gt; {// Sets Database

console.log\(typeof i\) // string

console.log\(i\) // 'Hello World!'

}\)

db.set\('uniqueID', 42\).then\(i =&gt; {

console.log\(typeof i\) // number

console.log\(i\) // 42

}\)

db.set\('uniqueID', \['Hello World!', 10, \['What?', 'Another Array!'\]\]\).then\(i =&gt; {

console.log\(typeof i\) // object

console.log\(i\) // \['Hello World!', 10, \['What?', 'Another Array!'\]\]

console.log\(i\[2\]\) // \['What?', 'Another Array!'\]

}\)

\`\`\`

---

&lt;a name="fetch"&gt;&lt;/a&gt;\*\*.fetch\(ID\)\*\* - \*Fetches the data from the given ID\*

\*&gt; Returns NULL if no data\*

\`\`\`js

db.set\('TrueXPixelsID', 'Hello World!'\)

db.fetch\('TrueXPixelsID'\).then\(i =&gt; {

console.log\(typeof i\) // string

console.log\(i\) // 'Hello World'

}\)

db.set\('MorfixxID', 10\)

db.fetch\('MorfixxID'\).then\(i =&gt; {

console.log\(typeof i\) // number

console.log\(i\) // 10

}\)

db.set\('RevolxID', \['Coal', 'Silver', 'Wood'\]\)

db.fetch\('RevolxID'\).then\(i =&gt; {

console.log\(typeof i\) // object

console.log\(i.length\) // 3

console.log\(i\) // \['Coal', 'Silver', 'Wood'\]

console.log\(i\[2\]\) // 'Wood'

}\)

db.set\('ExtasyID', { username: 'main', money: 100, items: \['Wood', 'Stone'\]}\)

db.fetch\('ExtasyID'\).then\(i =&gt; {

console.log\(typeof i\) // object

console.log\(i\) // { username: 'main', money: 100, items: \['Wood', 'Stone'\]}

console.log\(i.username\) // 'main'

console.log\(i.items\) // \['Wood', 'Stone'\]

console.log\(i.items\[0\]\) // 'Wood'

}\)

\`\`\`

---

&lt;a name="delete"&gt;&lt;/a&gt;\*\*.delete\(ID\)\*\* - \*Deletes the specified ID & data from the database\*

\*&gt; Returns a boolean, based on if it deleted the object or not\*

\`\`\`js

db.set\('uniqueID', 'Hello World!'\)

db.fetch\('uniqueID'\).then\(i =&gt; {

console.log\(i\) // 'Hello World'

}\)

db.delete\('uniqueID'\)

db.fetch\('uniqueID'\).then\(i =&gt; {

console.log\(i\) // NULL

}\)

\`\`\`

---

&lt;a name="push"&gt;&lt;/a&gt;\*\*.push\(ID, data\)\*\* - \*Pushes data to an array within the database\*

\*&gt; Returns new data, or a non-breaking error message if you aren't pushing to an array.\*

\`\`\`js

db.set\('uniqueID', \['Hello', 100\]\)

db.fetch\('uniqueID'\).then\(i =&gt; {

console.log\(i\) // \['Hello', 100\]

}\)

db.push\('uniqueID', 'World!'\)

db.fetch\('uniqueID'\).then\(i =&gt; {

console.log\(i\) // \['Hello', 100, 'World!'\]

}\)

\`\`\`

---

&lt;a name="add"&gt;&lt;/a&gt;\*\*.add\(ID, number\)\*\* - \*Adds the specified amount to a pre-defined number\*

\*&gt; Returns the new number, if either supply/target is not a number, it supplies a non-breaking error.\* \*\*If target was not defined previously, it automatically turns it in a number, and adds the specified amount.\*\*

\`\`\`js

db.set\('uniqueID', 100\)

db.fetch\('uniqueID'\).then\(i =&gt; {

console.log\(i\) // 100

}\)

db.add\('uniqueID', 400\)

db.fetch\('uniqueID'\).then\(i =&gt; {

console.log\(i\) // 500

console.log\(typeof i\) // 'number'

}\)

\`\`\`

---

&lt;a name="subtract"&gt;&lt;/a&gt;\*\*.subtract\(ID, number\)\*\* - \*Subtracts the specified amount to a pre-defined number\*

\*&gt; Returns the new number, if either supply/target is not a number, it supplies a non-breaking error.\* \*\*If target was not defined previously, it automatically turns it in a number, and subtracts the specified amount.\*\*

\`\`\`js

db.set\('uniqueID', 500\)

db.fetch\('uniqueID'\).then\(i =&gt; {

console.log\(i\) // 500

}\)

db.subtract\('uniqueID', 400\)

db.fetch\('uniqueID'\).then\(i =&gt; {

console.log\(i\) // 100

console.log\(typeof i\) // 'number'

}\)

\`\`\`

---

\#\# &lt;a name="FAQ"&gt;&lt;/a&gt;Frequently Asked Questions

&gt; How do I submit feedback, or suggest new features?

You can find a form \[here\]\([https://goo.gl/forms/KgjhQdWrztUfwHLB2\](https://goo.gl/forms/KgjhQdWrztUfwHLB2%29\).

&gt; What happens if I fetch an ID without assigning any data to it.

It will return \`NULL\`.

&gt; Where can I get support for Quick.db?

You can check out our \[Discord\]\([https://discord.io/plexidev\)!](https://discord.io/plexidev%29!) In addition to support we have a great community.

&gt; Is there a tutorial on Quick.db?

Not yet, although it was designed to be easy to learn, most can be found through the support Discord or documentation.

&gt; Do you have a YouTube channel?

Okay, well it wasn't actually frequently asked but I wanted to plug it anyways. Yes! I do have one here: [https://www.youtube.com/c/TrueXPixels](https://www.youtube.com/c/TrueXPixels)

---

\#\# &lt;a name="projects"&gt;&lt;/a&gt;Projects Using Quick.db

\*\[How do I get here?\]\([https://goo.gl/forms/KgjhQdWrztUfwHLB2\)\*](https://goo.gl/forms/KgjhQdWrztUfwHLB2%29*)

\*\*\[Plexi Development\]\([https://discord.io/plexidev\)\*\*](https://discord.io/plexidev%29**) - \*A majority of the server features on Plexi Development's Discord use Quick.db to store data.\*

\*Over \*\*133\*\* public programs also use \*\*Quick.db\*\* as a dependent!\* \[Source\]\([https://github.com/TrueXPixels/quick.db/network/dependents](https://github.com/TrueXPixels/quick.db/network/dependents%29\)

---

\*You've reached the end!\*

