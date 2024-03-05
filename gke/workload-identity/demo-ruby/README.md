<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/demo-apps/blob/main/gke/workload-identity/demo-ruby/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

# Sinatra Demo Backend App

This backend app that is useful for demonstration purposes.  It simply provides an endpoint that returns the number 42. It is a Sinatra Ruby app.

## Install

To install the dependencies.

    git clone git@github.com:boltops-pro/demo-apps
    cd gke/workload-identity/ruby
    bundle

## Start Server Locally

Start app with `bin/web`. Example:

    $ bin/web
    == Sinatra (v2.0.5) has taken the stage on 8080 for development with backup from Puma
    Puma starting in single mode...
    * Version 3.12.0 (ruby 2.5.3-p105), codename: Llamas in Pajamas
    * Min threads: 0, max threads: 16
    * Environment: development
    * Listening on tcp://0.0.0.0:8080
    Use Ctrl-C to stop

The backend app runs on port 8080.

Test with curl:

    $ curl localhost:8080
    42

## Confirm

    kubens demo-dev
    kubectl exec -ti deploy/web -- bash
    curl -H "Metadata-Flavor: Google" http://169.254.169.254/computeMetadata/v1/instance/service-accounts/default/email ; echo
    gcloud secrets list
