<!-- note marker start -->
**NOTE**: This repo contains only the documentation for the private BoltsOps Pro repo code.
Original file: https://github.com/boltopspro/demo-apps/blob/master/ruby/rails/frontend/README.md
The docs are publish so they are available for interested customers.
For access to the source code, you must be a paying BoltOps Pro subscriber.
If are interested, you can contact us at contact@boltops.com or https://www.boltops.com

<!-- note marker end -->

# Rails Demo Frontend App

The demo frontend app is useful for demonstration purposes.  The frontend app calls the [backend demo app](https://github.com/boltopspro-docs/demo-backend) and echos back the response.

## Install

To install the dependencies.

    git clone git@github.com:boltops-pro/demo-apps
    cd ruby/sinatra/frontend
    bundle

## Start Server Locally

Start app with `bin/web`. Example:

    $ bin/web
    => Booting Puma
    => Rails 7.0.3.1 application starting in development
    => Run `bin/rails server --help` for more startup options
    Puma starting in single mode...
    * Puma version: 5.6.4 (ruby 3.1.1-p18) ("Birdie's Version")
    *  Min threads: 5
    *  Max threads: 5
    *  Environment: development
    *          PID: 31275
    * Listening on http://0.0.0.0:8081
    Use Ctrl-C to stop

The frontend app runs on port 8081. The frontend app simply makes a network call to the backend app and echos back the response.

Make sure you have the backend app running. Here's the [backend app](../backend)

Test with curl:

    $ curl localhost:8081
    frontend calling backend. response from backend: {"status":"ok","db":[],"redis":"PONG"}

## Environment Variables

Notable environment variables.

Name | Example | Default
---|---|---
BACKEND_ENDPOINT | http://localhost:8080 | http://localhost:8080
