# Second Regular Laboratory

### Exercise:

Vulnerable Package:
- [local-devices](https://www.npmjs.com/package/local-devices) v2.0.0

Command to Download it:
```bash
$ npm i local-devices@2.0.0
```

Vulnerability Type:

- CWE-78: Improper Neutralization of Special Elements used in an OS Command (OS Command Injection)

"Source-Sink" Pair Location:

- Source at `local-devices/src/index.js#L16`:
```js
module.exports = function findLocalDevices(address)
```

- Sink at `local-devices/src/index.js#L114`:
```js
return cp.exec('arp -n ' + address).then(parseOne)
```

Valid Proof-Of-Concept Exploit:

- [Exploit.js](./POC/Exploit.js)

Valid Patch:

- By adding it at the beggining of `findLocalDevices` Function at `local-devices/src/index.js#L16-L25`:
```js
address = address.trim().split(' ')[0]
```
