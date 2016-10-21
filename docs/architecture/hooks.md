# Hooks

![Hooks](https://raw.githubusercontent.com/gcba-iris/iris-tech-docs/master/images/architecture/hooks.png)


## Description

A hook is just a callback function that gets executed when the data comes in or out the [dispatcher](dispatcher.md) for a given data flow. Multiple hooks can be tied to a single data flow, which in turn is tied to a single tag. Each hook can be set to run when the data comes in (input hook) or when the response goes out (output hook).

The hooks have read-only access to the data/response objects.

Hooks must extend the base Hook class.


## Difference with handlers

The handler can generate and return a response. Hooks can run on the response as well on the data.


## Exposed Methods

### Methods that must be implemented

- **process(data)** - The hook body, the function that will be executed.

### Methods present in the base class

- **run(data)** - Receives the data from the dispatcher and calls `process()`.


## Exposed Properties

### Getters that must be implemented

- **path** *(string)* - Returns the path of the dock file.
Example:
```javascript
    get path() {
        return __filename;
    }
```

### Getters present in the base class

- **name** *(string)* - Returns the handler name.
- **config** *(string)* - Returns the config object.

### Setters present in the base class

- **config** *(string)* - Sets the config object.


## Events

### Emits

- **data** - Triggered every time the hook receives a new piece of data/response.