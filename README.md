# NKSave

A Profile.save decryptor for Bloons td 6 (btd6)

Heavily inspired by [averysumener's c++ Profile.save thingy](https://github.com/averysumner/monke/) and [BowDown097](https://github.com/BowDown097)'s provided c# code. This would not have been possible without them.

# usage

## unpacking

just some standard stuff, did something a bit different using promisify in this example

```js
const nksave = require('nksave');
const fs = require('fs');

const { promisify } = require('util');
const readFile = promisify(fs.readFile);

async function main() {
    let bytes = await readFile('./path/to/Profile.save', null);
    let json = nksave.unpack(bytes);
    // log it, write to file, etc
}
main();
```

## packing

similar to above example

```js
const nksave = require('nksave');
const fs = require('fs');

const { promisify } = require('util');
const readFile = promisify(fs.readFile);
const writeFile = promisify(fs.readFile);

async function main() {
    let bytes = await readFile('./path/to/editedfile.json', null);
    let encoded = nksave.pack(bytes);
    await writeFile('./path/to/Profile.save', encoded);
}
main();
```
