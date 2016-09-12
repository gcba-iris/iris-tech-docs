# Services

![Services](https://raw.githubusercontent.com/gcba-iris/iris-tech-docs/master/images/architecture/services.png)

## Description

Services encapsulate functionality that may be used by more that one [handler](handlers.md) such as a database connection, a shared object, etc. With services it's possible to extract and reuse common pieces of code, keeping the handlers lean.


## Exposed Methods

- **setup()** - Initializes the service.

Each service shall expose custom methods.


## Events

Each service shall emit and listen to custom events, if any.


## Configuration

Each service shall take custom configuration parameters, if any.