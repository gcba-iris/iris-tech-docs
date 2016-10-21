# Handlers

![Handlers](https://raw.githubusercontent.com/gcba-iris/iris-tech-docs/master/images/architecture/handler.png)


## Description

Processes the data object sent by the [dispatcher](dispatcher.md). A handler can generate a response, which is passed back to the dispatcher. Said response can be a string, an array, an object with a `toString()` method or a javascript object analogous to the `data.message` object. The response will be serialized and sent by the respective [dock](docks.md). If there's no response, the data flow ends there.

There can only be a single handler in a data flow, which in turn is defined by a single tag. This means that for each tag there's only one data flow with one handler at the end. The tag is comparable to a MVC route and the handler to a MVC controller: a handler only processes the data that arrives with a certain tag.

Handlers must extend the base Handler class.


## Difference with hooks

The handler can generate and return a response. Hooks can run on the response as well on the data.


## Exposed Methods

### Methods that must be implemented

- **process(data)** - Processes the data object.

### Methods present in the base class

- **handle(data)** - Receives the data from the dispatcher and calls `process()`.
- **send(reponse)** - Sends the response to the dispatcher.


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

- **data** - Triggered every time the handler receives a new piece of data.