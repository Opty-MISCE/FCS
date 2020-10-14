# Second Laboratory

### Exercise:

Vulnerability Type:

- CWE-78: Improper Neutralization of Special Elements used in an OS Command (OS Command Injection)

"Source-Sink" Pair Location:

- Source: [Here](./local-devices/src/index.js#L16)
```js
module.exports = function findLocalDevices(address)
```

- Sink: [Here](./local-devices/src/index.js#L114)
```js
return cp.exec('arp -n ' + address).then(parseOne)
```

Valid Proof-Of-Concept Exploit:

- [Exploit.js](./POC/Exploit.js)

Valid Patch:

- By adding it at the beggining of [`findLocalDevices`](./local-devices/src/index.js#L16-L25):
```js
address = address.trim().split(' ')[0]
```

