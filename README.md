# Vision

Iris is a modular, extensible, real-time IoT backend. It receives raw data from devices and pipes it through a customizable process line. Write services that run analytics, store the data, send it somewhere else, etc. Or combine a buch of existing plugins to build the ultimate data flow. Iris gives you total freedom with the peace of mind of a stable, rock solid foundation.

While Iris's strength lies in swallowing up loads of real-time data, it can also send responses back. Spin up an API to query the data, send commands to the devices... the possibilities are endless.


## Principles

**1. Modularity**

Iris should be thought of as a collection of loosely coupled components implementing a clear and well known interface. Must be developed as a series of distinct modules.

**2. Extensibility**

The user should be able to write custom components, and/or throw in existing ones. They must all be hot swappable, with the exception of the [dispatcher](docs/architecture/dispatcher.md).

**3. Statelessness**

The kind of processing a piece of raw data goes through must be dictated only by the tags present in the data itself. Iris shouldn't know a thing about the data source.

**4. Flexibility**

Iris should support a unique data flow for each tag.

**5. Stability**

Iris should run in multiple fail-safe threads. The failures should be handled gracefully in order to maximize uptime. Also there must be a full test suite, aiming for 100% coverage.


## License

    MIT License

    Copyright (c) 2016+ Buenos Aires City Government

    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    SOFTWARE.
