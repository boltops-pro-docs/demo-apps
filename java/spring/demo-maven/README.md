<!-- note marker start -->
**NOTE**: This repo contains only the documentation for the private BoltsOps Pro repo code.
Original file: https://github.com/boltopspro/demo-apps/blob/master/java/spring/demo-maven/README.md
The docs are publish so they are available for interested customers.
For access to the source code, you must be a paying BoltOps Pro subscriber.
If are interested, you can contact us at contact@boltops.com or https://www.boltops.com

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
