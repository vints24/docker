Docker Sonar 4.4 container
======

This repository contains a SonarQube installation with the following software installed:

* MySQL server
* SonarQube 4.4

## Getting the container

You can get the image by running, this will install this image into your local docker repository.

```
docker pull gjong/sonar
```

## Running the container

When the container starts it will automatically start the SonarQube server and MySQL. To enable analyses using the
container the following ports are exposed:

* port 9000   -> running SonarQube
* port 3306	  -> exposing the mysql connection (may be needed in the mvn sonar:sonar call)

You can run the container with access to the webserver by running:

```
docker run -d -p 9000:9000 -p 3306:3306 gjong/sonar
```

If you want to create a image that can easily be restarted then do the following:

```
docker run -d -p 9000:9000 -p 3306:3306 gjong/sonar --name sonarqube
```

To restart the image without loosing the data simply run:

```
docker start -p 9000:9000 -p 3306:3306 sonarqube
```


The default account installed for sonar is admin/admin. For restarting SonarQube after installing new modules or
updating modules you can stop and restart the container.