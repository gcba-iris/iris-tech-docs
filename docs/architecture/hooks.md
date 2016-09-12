# Hooks

![Hooks](http://i.imgur.com/myOoPdd.png)


## Description

A hook is just a callback function that gets executed when the data comes in or out the [dispatcher](dispatcher.md) for a given data flow. Multiple hooks can be tied to a data flow, which in turn is tied to a particular header. Each hook can be set to run when the data comes in (input hook) or when the response goes out (output hook).

The hooks have read-only access to the data/response objects.


## Exposed Methods

- **setup()** - Initializes the hook.
- **run()** - Executes the hook.


## Events

### Emits

- **onLoad:** When the hook has been loaded for the first time (initial load).
- **onReload:** Fired when the hook has been hot reloaded.