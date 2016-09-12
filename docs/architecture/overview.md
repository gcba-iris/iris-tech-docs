## Logical Architecture
![Logical Architecture](http://i.imgur.com/JNIo0Sh.png)

### Flow

1. Data pours in from multiple sources through the [docks](docks.md). Each dock accounts for a single protocol, and listens to one or more ports.
2. The dock parses the data and converts it to a standardized javascript object.
3. The dock sends it to the [dispatcher](dispatcher.md).
4. The dispatcher looks at the header property and routes the data to the right [handler](handlers.md).
5. As the data makes its way to the handler, the [input hooks](hooks.md) (read-only middlewares) can access it and do stuff with it. But they can't modify it.
6. The handler process the data, making use of [services](services.md) to persist it, redirect it, etc.
7. If the handler generates a response, it goes to the dispatcher. If there's no response, the process ends here.
8. The [output hooks](hooks.md) can get their hands on the response and do stuff with it, but without being able to modify it.
8. Then the dispatcher gets the response and routes it to the right dock.
9. The dock sends it back to the original device.


#### Headers

Each header in a raw data packet defines a **data flow**. And each data flow is put together by stacking components on a pipeline. It is akin to the request/response cycle in a regular web application. A single data flow is made up of two phases:

##### Input flow

Represents the path a piece of raw data takes from the device to a single handler. Input hooks are executed along the way.

##### Output flow

The response making its way back to the same device. Output hooks are executed along the way. This flow is dependent on the existence of a response; if the handler generates no response, the input flow is all there is.

#### Components

**Docks**, **hooks**, **handlers** and **services** can be third-party packages or custom code. They should all be hot-swappable, and reload automatically on change without restarting Iris.

#### Parsers

While the dock base class will include a generic parser (with configurable data and header delimiters), it must be possible to pass in a custom parser function.

#### Threads

Iris must span on boot a fixed, configurable number of threads that kick in and handle the data after the dispatcher routes it. Each thread should be able to handle by itself a data flow back-to-back. This allows parallell processing and increases stability and data processing speed.


## Physical Architecture
![Physical Architecture](http://i.imgur.com/FcOokpX.png)

Iris is designed to sit right in front of the data generating devices. Once the raw data has been processed, Iris can pass it on to other services.

### Stack

Iris uses no database by default, and has no UI. Regarding reverse proxies, Iris should access the system ports directly. Though it should be possible to run an array of Iris instances behind a load balancer.

- Node.js 6+