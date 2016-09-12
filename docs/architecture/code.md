# Code

The code and all related project files will be hosted in the [gcba-iris](https://github.com/gcba-iris) GitHub organization:

1. **Code**

    [https://github.com/gcba-iris/iris](https://github.com/gcba-iris/iris)

2. **Technical Documentation**

    [https://github.com/gcba-iris/iris-tech-docs](https://github.com/gcba-iris/iris-tech-docs)

The javascript version used will be a subset of ES6, with only the features supported by Node.js 6.5.0 without runtime flags ([shipping features](https://nodejs.org/en/docs/es6/)).


## Conventions

This project will adopt the [Airbnb javascript style guide](https://github.com/airbnb/javascript), with the following differences:

- Do call Object.prototype methods directly. ([3.9](https://github.com/airbnb/javascript#objects--prototype-builtins))
- The soft tabs will be set to 4 spaces, not 2. Actual tabs are not allowed. ([18.1](https://github.com/airbnb/javascript#whitespace--spaces))
- The lines of code must be 120 characters max, not 100. ([18.12](https://github.com/airbnb/javascript#whitespace--max-len))
- No additional trailing comma. ([19.2](https://github.com/airbnb/javascript#commas--dangling))
- Do use javascript getters/setters. ([23.2](https://github.com/airbnb/javascript#accessors--no-getters-setters))


## Testing

The testing framework used will be [tape](https://github.com/substack/tape). The following types of tests will be written:

- Unit
- Integration
- End-to-end

The unit tests should account for the majority of the test suite.

