<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/demo-apps/blob/main/java/spark/backend/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

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

