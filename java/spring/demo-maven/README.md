<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/demo-apps/blob/main/java/spring/demo-maven/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

# Demo App to Show Maven Usage

The main file is [pom.xml](pom.xml). This defines scripts and project dependencies.

## Usage

Example commands:

    mvn clean install                         # compiles project
    java -jar target/demo-0.0.1-SNAPSHOT.jar  # starts up webserver

The server starts at: http://localhost:8080/

Altogether

    mvn clean install && java -jar target/demo-0.0.1-SNAPSHOT.jar

## Test URLs

URL | Description
---|---
http://localhost:8080/ | Home page. Returns simple text string.

Example curl tests

    $ curl localhost:8080
    Hello World
