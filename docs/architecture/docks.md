# Docks

![Docks](http://i.imgur.com/5zTvlVJ.png)

## Description

Listens to one or more ports for incoming raw data through a specific protocol. Parses it and converts it to a javascript object. Then passes this object along to the [dispatcher](dispatcher.md). If a response comes back, the dock serializes it and sends it off to the original source.

More that one dock can be arranged for a single protocol, provided that they listen to different ports.

## Exposed Methods

- **setup()** - Initializes the dock.
- **listen()** - Listens to the specified ports.
- **parse()** - Parses the raw data and converts it to a javascript object. The default implementation is inherited from the base class, but can be overriden.
- **pass()** - Passes the data along to the dispatcher.
- **encode()** - Serializes the response. The default implementation can be overriden.
- **reply()** - Sends the response.

## Events

### Emits
- **onData:** Triggered every time the dock receives a new piece of data. Gives the handler access to the raw, unprocessed data. Useful to proxy it somewhere else.

## Configuration

- **ports** *(array)*: The ports to listen to.
- **parser** *(function)*: Custom function that parses the data.
- **encoder** *(function)*: Custom function that encodes the response.