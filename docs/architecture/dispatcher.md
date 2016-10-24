# Dispatcher

![Dispatcher](https://raw.githubusercontent.com/gcba-iris/iris-tech-docs/master/images/architecture/dispatcher.png)


## Description

Receives the data object from the [dock](docks.md), calls the registered [input hooks](hooks.md) and routes the data to the right [handler](handlers.md). Similarly, when there's a response the dispatcher routes it to the right dock and executes the registered [output hooks](hooks.md).

The dispatcher is the only piece of Iris that cannot be customized or swapped off - it's the glue that holds everything together.


## Exposed Methods

- **dispatch(data, callback)** - Routes the data objects to the right handlers. If there's a callback coming fron the dock, the dispatcher passes it along to the thread pool to be executed if there's a response.
- **respond(response)** - Sends the responses to the right dock.


## Events

### Emits

- **data** - Triggered every time the dispatcher receives a new piece of data.
- **dispatch** - When a piece of data has been delivered to its handler.
- **respond** - Triggered when a response has ben sent to a dock.

### Listens

- **reload** - Hot reloads every module in the threadpool when a change in any of them is detected. If the changed module is a dock, only stops and restarts that dock.