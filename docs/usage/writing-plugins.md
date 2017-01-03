# Writing Plugins

Plugins are javascript files or npm packages that get required in the Irisfile. All plugins extend some base class.

## Docks

You must implement `get path()`, `listen()` and `stop()`. `send()` is optional.

- **get path():** returns the dock path in the filesystem.
- **listen():** starts listening at the configured port.
- **stop():** stops listening.
- **send(response):** sends the response to the device.

Take a look at the [base class](architecture/docks.md) for a list of the available methods and events, like `this.process()`.

### Sample HTTP dock

```javascript
'use strict';

const Dock = require('iris').Dock;
const http = require('http');
const requestIp = require('request-ip');

class HTTPDock extends Dock {
    constructor(name, protocol) {
        super(name, protocol);

        this._server = null;
        this._listening = false;
    }

    get path() {
        return __filename;
    }

    listen() {
        this._server = http.createServer(this._handleRequest.bind(this));

        if (!this._listening) {
            this._server.listen(this.config.port, () => {
                this._listening = true;
                this.logger.info('[HTTP Dock] Listening on port ' + this.config.port + '...');
            });
        }
    }

    stop() {
        if (this._listening) {
            this._server.close();
            this._listening = false;
            this.logger.info('[HTTP Dock] Stopped listening');
        }
    }

    _handleRequest(request, response) {
        const chunks = [];
        const meta = {
            ip: requestIp.getClientIp(request)
        };

        request.on('data', function (chunk) {
            chunks.push(chunk);
        });

        request.on('end', function () {
            const data = Buffer.concat(chunks);

            this.process(data, meta, (message) => {
                response.statusCode = 200;

                if (message) {
                    response.write(message);
                    this.logger.verbose('Sent response to client');
                } else response.end();
            });
        }.bind(this));
    }
}

module.exports = new HTTPDock('http', 'HTTP');
```

## Handlers

You must implement `get path()` and `handle()`.

- **get path():** returns the handler path in the filesystem.
- **handle(data):** does with the data whatever the handler was meant to do.

Take a look at the [base class](architecture/handlers.md) for a list of the available methods and events.

### Sample handler

```javascript
'use strict';

const Handler = require('iris').Handler;

class Handler1 extends Handler {
    constructor(name) {
        super(name);
    }

    get path() {
        return __filename;
    }

    handle(data) {
        this.logger.info('[Handler1] Handling data...');

        return 'A response';
    }
}

module.exports = new Handler1('handler1');
```

## Hooks

You must implement `get path()` and `process()`.

- **get path():** returns the hook path in the filesystem.
- **process(data):** does with the data whatever the hook was meant to do.

Take a look at the [base class](architecture/hooks.md) for a list of the available methods and events.

### Sample hook

```javascript
'use strict';

const Hook = require('iris').Hook;

class Hook1 extends Hook {
    constructor(name) {
        super(name);
    }

    get path() {
        return __filename;
    }

    process(data) {
        this.logger.info('[Hook1] Running...');
    }

}

module.exports = new Hook1('hook1');
```

## Utilities

### Logger

Iris exposes a [Winston](https://github.com/winstonjs/winston) instance at several points, available for full use and configuration:

- **At each base class:** for plugins's use. Accesible at `this.logger`.
- **At the Iris instance itself:** for Irisfile and other scripts's use. Accesible at `iris.logger`.