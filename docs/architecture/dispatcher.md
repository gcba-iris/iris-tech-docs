# Dispatcher

![Dispatcher](http://i.imgur.com/1Lg4L15.png)

## Description

Receives the data objects from the [docks](docks.md) and routes them to the right [handlers](handlers.md). Then calls the registered [input hooks](hooks.md) for the corresponding headers. Similarly, when there's a response the dispatcher routes it to the right dock and executes the registered [output hooks](hooks.md). 

The dispatcher is the only piece of Iris that cannot be customized or swapped off - it's the glue that holds everything together.


## Exposed Methods

- **setup()** - Initializes the dispatcher.
- **dispatch()** - Routes the data objects to the right handlers and calls the registered input hooks.
- **respond()** - Sends the responses to the right dock and executes the registered output hooks.


## Events

### Emits

- **onData:** Triggered every time the dispatcher receives a new piece of data.
- **onDispatch:** When a piece of data has been delivered to its handler.
- **onRespond:** Triggered when a response has ben sent to a dock.
- **onHookRegistered:** Fired when a hook is registered in the input or output phase of a data flow.
- **onHookUnregistered:** When a hook is unregistered from the input or output phase of a data flow.