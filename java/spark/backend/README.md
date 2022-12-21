<!-- note marker start -->
**NOTE**: This repo contains only the documentation for the private BoltsOps Pro repo code.
Original file: https://github.com/boltopspro/demo-apps/blob/master/java/spark/backend/README.md
The docs are publish so they are available for interested customers.
For access to the source code, you must be a paying BoltOps Pro subscriber.
If are interested, you can contact us at contact@boltops.com or https://www.boltops.com

<!-- note marker end -->

## Usage

Build

    mvn package

Run

    java -jar target/demo-1.0-SNAPSHOT.jar

This starts up a server on localhost:4567. Here are test endpoints.

    $ curl localhost:4567/
    Hello World
    $ curl localhost:4567/hello
    Hello World again
    $

