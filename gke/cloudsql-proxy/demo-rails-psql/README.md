<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/demo-apps/blob/main/gke/cloudsql-proxy/demo-rails-psql/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

# Rails Demo App

This backend app that is useful for demonstration purposes.  It simply provides an endpoint that returns the number 42.

## Install

To install the dependencies.

    git clone git@github.com:boltops-pro/demo-apps
    cd ruby/rails/backend
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
    *          PID: 29623
    * Listening on http://0.0.0.0:8080
    Use Ctrl-C to stop

The backend app runs on port 8080.

The backend comes with URLs to test connections to:

* MySQL DB: http://localhost:8080/up/db
* Redis:    http://localhost:8080/up/redis

And the homepage tests both:

* Homepage: http://localhost:8080/

Example tests with curl:

    $ curl localhost:8080
    {"status":"ok","db":[]}

## Environment Variables

Notable environment variables.

Name | Example | Default
---|---|---
DATABASE_URL | mysql2://root:Secret123@10.12.2.3/backend | (not set)

## Debugging

    mysql -uroot -p -h10.12.0.5 # private IP
    mysql -uroot -p -h127.0.0.1 # via cloudsql proxy. works if cloudsql sidecar properly running
