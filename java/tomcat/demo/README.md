<!-- note marker start -->
**NOTE**: This repo contains only the documentation for the private BoltsOps Pro repo code.
Original file: https://github.com/boltopspro/demo-apps/blob/master/java/tomcat/demo/README.md
The docs are publish so they are available for interested customers.
For access to the source code, you must be a paying BoltOps Pro subscriber.
If are interested, you can contact us at contact@boltops.com or https://www.boltops.com

<!-- note marker end -->

# Demo Java Web App

[![BoltOps Badge](https://img.boltops.com/boltops/badges/boltops-badge.png)](https://www.boltops.com)

Simple java project demos how to build a war file to be deployed on a Tomcat server.

## Build

The build script uses `mvn package` to produce a demo.war file and then bundles it with a Docker image that runs Tomcat.  Usage:

    bin/build

This script calls `mvn package` and moves the `target/demo.war` to `pkg/demo.war`

Here's an example of some things to check after running the build script:

    $ ls pkg/demo.war
    pkg/demo.war
    $ docker images
    REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
    demo-java           latest              88092dfb7325        6 minutes ago       591MB
    tomcat              8.5                 a92c139758db        2 weeks ago         558MB
    $

## Source Url Mapping

The app is a small demo of a java servlet app.  Here's the source code to url mapping:

Source | Url
--- | ---
src/main/java/Hello.java | localhost:8080/demo/Hello
src/main/webapp/index.jsp | localhost:8080/demo/index.jsp

## Docker Run

Here are the summarized commands to run and test that Tomcat is serving the war file:

    bin/build # to build pkg file
    docker build -t demo-java .
    docker run --rm -p 8080:8080 -d demo-java
    docker exec -ti $(docker ps -ql) bash
    curl localhost:8080/demo/Hello
    curl localhost:8080/demo/index.jsp
    exit
    docker stop $(docker ps -ql)

Then you can hit the the [HOSTNAME]:8080/demo/Hello and to verify that Tomcat is servering the demo.war file.  You should see an html page that says "Hello World".  The output should look similar:

    $ docker run --rm -p 8080:8080 -d demo-java
    2ba7323481fa5c4068b90f2edf38555d9551303e9c2e4c27137ab0545688555b
    $ docker exec -ti $(docker ps -ql) bash
    root@2ba7323481fa:/opt/tomcat# curl localhost:8080/demo/Hello
    <h1>Hello World Hello.java</h1>
    root@2ba7323481fa:/opt/tomcat# curl localhost:8080/demo/index.jsp
    <html>
    <body>
    <h2>Hello World index.jsp!</h2>
    </body>
    </html>
    root@2ba7323481fa:/opt/tomcat# exit
    exit
    $ docker stop $(docker ps -ql)
    2ba7323481fa
    $ docker ps -a
    CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
    $

## Initial Generation

Here are some notes on the initial generation of the project. The initial files and project structure was generated with the `mvn archetype:generate` command.  Note, you do not have to run the command it is just noted here for posterity.  More info: [Creating a webapp](https://maven.apache.org/plugins-archives/maven-archetype-plugin-1.0-alpha-7/examples/webapp.html) and [Introduction to the Standard Directory Layout](https://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html).

Change were made like adding a simple [Hello.java](src/main/java/Hello.java) Serlvet class.

The original command was:

    mvn archetype:generate \
      -DinteractiveMode=false \
      -DgroupId=com.domain \
      -DartifactId=demo \
      -DarchetypeArtifactId=maven-archetype-webapp

## Dependencies

* docker: `brew install docker`
* maven: `brew install maven`
