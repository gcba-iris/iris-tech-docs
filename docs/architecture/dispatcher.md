# Dispatcher

![Dispatcher](http://i.imgur.com/EwlsOgr.png)

## Description

Receives the data objects from the docks and routes them to the right handlers. Then calls the registered input hooks for the corresponding headers.
Similarly, when there's a response the dispatcher routes it to the right dock and executes the registered output hooks. 

The dispatcher is the only piece of Iris that cannot be customized or swapped off - it's the glue that holds everything together.


## Exposed Methods

- **setup()** - Initializes the dispatcher.
- **dispatch()** - Routes the data objects to the right handlers and calls the registered input hooks.
- **respond()** - Sends the responses to the right dock and executes the registered output hooks.


## Events

### Emits
- **onHookRegistered:** Fired when a hook is registered for a header in an input or output flow.
- **onHookUnregistered:** When a hook is unregistered from an input ot output flow.