<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/demo-apps/blob/main/java/spring/demo-gradle/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

# Demo App to Show Gradle Usage

The main file is [build.gradle](build.gradle). This defines gradle scripts and project dependencies.

## Usage

Example commands:

    gradle clean build  # compiles project
    gradle bootrun      # starts up webserver

The server starts at: http://localhost:8080/

Altogether

    gradle clean build bootrun

## Test URLs

URL | Description
---|---
http://localhost:8080/ | Home page. Returns simple text string.

Example curl tests

    $ curl localhost:8080
    Hello World
