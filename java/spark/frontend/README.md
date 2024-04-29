<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/demo-apps/blob/main/java/spark/frontend/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

## Usage

Build

    mvn package

Run

    java -jar target/frontend-1.0-SNAPSHOT.jar

This starts up a server on localhost:4568. Here are test endpoints.

    $ curl localhost:4568
    frontend calling backend. backend response: Hello World
    $ curl localhost:4568/hello
    frontend hello world
    $

## Notes

The initial mvn command to generate the project was:

    mvn archetype:generate -DgroupId=frontend -DartifactId=frontend -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

The generated files were adjusted based on [this guide](https://pconrad-webapps.github.io/topics/sparkjava_getting_started/) to get the app running.
