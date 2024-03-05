<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/demo-apps/blob/main/java/spring/frontend-maven/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

## Usage

Build and run.

    bin/build # calls `mvn clean install`
    bin/web   # starts spring boto server

This starts up a web server on localhost:8080

## Migrations

Using flyaway to create a posts table and seed it with some data. Note, migrations are ran as part of

    mvn clean install

## Test URLs

URL | Description
---|---
http://localhost:8080/ | Home page. Returns simple text string.
http://localhost:8080/test/db | Returns posts records from DB.
http://localhost:8080/test/redis | Test redis set and get operations and return value.

Example curl tests

    $ curl localhost:8080
    Hello World. SQL: 1
    $ curl localhost:8080/test/db
    [{"id":1,"title":"post 1","body":"test 1"},{"id":2,"title":"post 2","body":"test 2"}]
    $ curl localhost:8080/test/redis
    value1
    $

## Environment Variables

Notable environment variables.

Name | Example | Default
---|---|---
DB_HOST | 10.0.0.1 | 127.0.0.1
DB_NAME | demo_dev | demo_dev
DB_USER | deploy | root
DB_PASS | password | ''
REDIS_HOST | 10.0.0.2 | 127.0.0.1

## Docker Build and Run

    docker build -t demo-spring .
    docker run --rm -p 8080:8080 -d demo-spring
    docker exec -ti $(docker ps -ql) bash
    curl localhost:8080/demo/Hello
    curl localhost:8080/demo/index.jsp
    exit
    docker stop $(docker ps -ql)
