Docker Apache 2 webserver
======

This repository allows for building a docker image from the latest ubuntu version with the following applications pre-installed:

* Apache 2.x
* PHP 5.x
* MySQL server

## Getting the container

You can get the image by running, this will install this image into your local docker repository.

```
docker pull gjong/apache
```

## Running the container

When the container starts it will automatically start the Apache webserver and MySQL. The Apache server will be running
on port 80, which is also exposed out of the container.

You can run the container with access to the webserver by running:

```
docker run -d -p 80:80 gjong/apache