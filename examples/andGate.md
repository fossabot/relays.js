![AND Gate Diagram](andGate/diagram.png)

An example implementation of relays.

```js
const Relay = require('../../index.js');

const AndGate = new Relay((a, b) => a && b);
const AndGateInputA = new Relay(x => typeof x === 'boolean' && x);
const AndGateInputB = new Relay(x => typeof x === 'boolean' && x);

AndGateInputA.connectTo(AndGate);
AndGateInputB.connectTo(AndGate);

AndGate.pass(x => console.log('The result is ' + x));

AndGateInputA.receive(true);
AndGateInputB.receive(true);

AndGateInputA.receive(true);
AndGateInputB.receive(false);

AndGateInputA.receive(false);
AndGateInputB.receive(true);

AndGateInputA.receive(false);
AndGateInputB.receive(false);
```

example output:

```bash
$ node examples/andGate
The result is true
The result is false
The result is false
The result is false
```