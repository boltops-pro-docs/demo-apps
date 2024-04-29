<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/demo-apps/blob/main/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

# Demo Apps

[![BoltOps Badge](https://img.boltops.com/boltops/badges/boltops-badge.png)](https://www.boltops.com)

List of demo apps that can be used to demonstrate the [Reference Infrastructure](https://github.com/boltopspro/reference-infrastructure).

## Setup

    git clone git@github.com:boltopspro/demo-apps.git
    cd demo-apps
    git submodule init
    git submodule update

## Apps

The instructions to deploy each demo app are on their README.

* [Backend](https://github.com/boltopspro/demo-backend)
* [Frontend](https://github.com/boltopspro/demo-frontend)

### Add another project

To add an additional project as a submodule:

    git submodule add git@github.com:boltopspro/demo-backend apps/backend
