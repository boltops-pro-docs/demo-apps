<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/demo-apps/blob/main/java/spring/backend/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

## Usage

Build and run.

    bin/build # gradle clean build
    bin/web   # gradle runboot

This starts up a web server on localhost:8080

## Migrations

Using flyway to create a posts table and seed it with some data.

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

## Debugging

It's useful to deploy an image with `sleep infinity`, it's provided as a comment at the bottom of Docker file. Then `kubectl exec` into the container and run:

    mysql -u$DB_USER -h$DB_HOST -p$DB_PASS

To see if the app is successfully connecting to the DB and that it has the database.
