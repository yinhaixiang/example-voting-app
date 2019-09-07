Example Voting App
==================

This is an example Docker app with multiple services. It is run with Docker Compose and uses Docker Networking to connect containers together. You will need Docker Compose 1.6 or later.

More info at [https://blog.docker.com](https://blog.docker.com)

Architecture
-----

* A Python webapp which lets you vote between two options
* A Redis queue which collects new votes
* A Java worker which consumes votes and stores them in…
* A Postgres database backed by a Docker volume
* A Node.js webapp which shows the results of the voting in real time

![pic](architecture.png)

Running
-------

Run in this directory:
```
$ docker-compose build
$ docker-compose up
```
    

The app will be running on port 5000 on your Docker host, and the results will be on port 5001.
