<!-- note marker start -->
**NOTE**: This repo contains only the documentation for the private BoltsOps Pro repo code.
Original file: https://github.com/boltopspro/demo-apps/blob/master/java/spark/frontend/README.md
The docs are publish so they are available for interested customers.
For access to the source code, you must be a paying BoltOps Pro subscriber.
If are interested, you can contact us at contact@boltops.com or https://www.boltops.com

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
