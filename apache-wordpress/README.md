Docker Wordpress Apache server
======

This repository contains an image with Wordpress's latest release based upon the gjong/apache docker image. It contains:

* Apache 2.x, with PHP
* MySQL
* Wordpress

## Getting the container

You can get the image by running, this will install this image into your local docker repository.

```
docker pull gjong/apache-wordpress
```

## Running the container

When the container starts it will automatically start the Apache webserver with Wordpress installation and MySQL. The Apache server 
will be running on port 80, which is also exposed out of the container.

You can run the container with access to the webserver by running:

```
docker run -d -p 80:80 gjong/apache-wordpress
```

Once the container is running you will get a Wordpress website on http://localhost/ that still needs to be configured using
the installation script. 

For the database use the following settings:

Username: root
Password: <NONE>
Database: wordpress