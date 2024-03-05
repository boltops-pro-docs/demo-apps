<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/demo-apps/blob/main/ruby/sinatra/frontend/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

# Sinatra Demo Frontend App

The demo frontend app is useful for demonstration purposes.  The frontend app calls the [backend demo app](https://github.com/boltopspro/demo-backend) and echos back the response.  This is a Sinatra Ruby app.

## Install

To install the dependencies.

    git clone git@github.com:boltops-pro/demo-apps
    cd ruby/sinatra/frontend
    bundle

## Start Server Locally

Start app with `bin/web`. Example:

    $ bin/web
    == Sinatra (v2.0.5) has taken the stage on 8081 for development with backup from Puma
    Puma starting in single mode...
    * Version 3.12.0 (ruby 2.5.3-p105), codename: Llamas in Pajamas
    * Min threads: 0, max threads: 16
    * Environment: development
    * Listening on tcp://0.0.0.0:8081
    Use Ctrl-C to stop

The frontend app runs on port 8081. The frontend app simply makes a network call to the backend app and echos back the response.

Make sure you have the backend app running. Here's the [backend app](../backend)

Test with curl:

    $ curl localhost:8081
    frontend calling backend. response from backend: 42

## Environment Variables

Notable environment variables.

Name | Example | Default
---|---|---
BACKEND_ENDPOINT | http://localhost:8080 | http://localhost:8080
