# Vision

Iris is a modular, extensible, real-time IoT backend. It receives raw data from devices and pipes it through a customizable process line. Write services that run analytics, store the data, send it somewhere else, etc. Or combine a buch of existing plugins to build the ultimate data flow. Iris gives you total freedom with the peace of mind of a stable, rock solid foundation.

While Iris' strength lies in swallowing up loads of real-time data, it can also send responses back. Spin up an API to query the data, send commands to the devices... the possibilities are endless.


## Principles

**1. Modularity**

Iris should be thought of as a collection of loosely coupled components implementing a clear and well known interface. Must be developed as a series of modules tied together with a dependency injection container.

**2. Extensibility**

The user should be able to write custom components, and/or throw in existing ones. They must all be hot swappable, with the exception of the [dispatcher](docs/architecture/dispatcher.md).

**3. Statelessness**

The kind of processing a piece of raw data goes through must be dictated only by the headers present in the data itself. Iris shouldn't know a thing about the data source.

**4. Flexibility**

Iris should support a unique data flow for each header.

**5. Stability**

Iris should run in multiple fail-safe threads. The failures should be handled gracefully in order to maximize uptime. Also there must be a full test suite, aiming for 100% coverage.