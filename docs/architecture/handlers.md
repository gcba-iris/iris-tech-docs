# Handlers

![Handlers](http://i.imgur.com/ihDnlyA.png)


## Description

Processes the data objects sent by the [dispatcher](dispatcher.md). A handler can make use of various [services](services.md) to deal with the data. It can also generate a response, which is passed back to the dispatcher. Said response is a javascript object analogous to the data object that can be serialized and sent by the respective [dock](docks.md). If there's no response, the data flow ends there.

A handler belongs to a specific data flow, which in turn is defined by a specific data header. The header is comparable to a MVC route and the handler to a MVC controller: a handler only processes the data that arrives with a certain header. And for each header there's only one handler.


## Exposed Methods

- **setup()** - Initializes the handler.
- **handle()** - Processes the data object.


## Events

### Emits

- **onData:** Triggered every time the handler receives a new piece of data.
- **onLoad:** When the handler has been loaded for the first time (initial load).
- **onReload:** Fired when the handler has been hot reloaded.