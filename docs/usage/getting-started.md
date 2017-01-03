# Getting Started

## 1. Create an empty project

```bash
$ iris new myApp
```

Creates a new folder called `myApp` with the following contents:

```
myApp/
|___modules/
|   |___docks/
|   |___handlers/
|   |___hooks/
|___irisfile.js
|___package.json
```
Then runs `npm install`.


### Existing project

```bash
$ iris init
```

Creates an empty Irisfile and runs `npm install gcba-iris/iris --save`.

## 2. Add flows

The data flows are defined in the Irisfile, using `iris.flow()`.

### Method signature

```javascript
iris.flow(name, config);
```
- **name**: A string identifier.
- **config**: An object containing:
  - **tag**: A unique string.
  - **docks**: An array of dock instances.
  - **handler**: The handler instance.
  - **inputHooks** *(optional)*:  An array of hook instances.
  - **outputHooks** *(optional)*: An array of hook instances.

### Sample irisfile.js

```javascript
const iris = require('iris');
const dock = require('./docks/http');
const handler = require('./handlers/handler1');
const handler2 = require('./handlers/handler2');
const hook1 = require('./hooks/hook1');
const hook2 = require('./hooks/hook2');

iris.config = {
    threads: 4,
    logLevel: 'warn',
};

dock.config = {
    port: 5000
};

iris.flow('Flow 1', {
    tag: 'tag1',
    docks: [dock],
    handler: handler,
    inputHooks: [hook1],
    outputHooks: [hook2]
});

iris.flow('Flow 2', {
    tag: 'tag2',
    docks: [dock],
    handler: handler2,
    inputHooks: [hook2]
});
```

The default amount of threads is the number of CPU cores.

## 3. Run flows

Inside a project directory:

```bash
$ iris
```
![Iris screenshot](https://github.com/gcba-iris/iris/raw/master/assets/img/running.png)