FROM ubuntu

MAINTAINER Gerben Jongerius <g.jongerius@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

RUN alias adduser='useradd' && apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y mysql-server supervisor wget unzip

RUN wget http://dist.sonar.codehaus.org/sonarqube-4.4.zip --output-document=/tmp/sonarqube.zip
RUN unzip /tmp/sonarqube.zip -d /tmp/
RUN mkdir /opt/sonarqube && cp /tmp/sonarqube-4.4/* /opt/sonarqube/ -r

RUN apt-get -y install software-properties-common
RUN add-apt-repository ppa:webupd8team/java
RUN apt-get -y update && echo "oracle-java7-installer shared/accepted-oracle-license-v1-1 boolean true" | debconf-set-selections
RUN apt-get -y install oracle-java7-installer

RUN apt-get -y install openssh-server

# Setup the supervisor run template
ADD ./docker/mysql.conf /etc/supervisor/conf.d/mysql.conf
ADD ./docker/sonar.conf /etc/supervisor/conf.d/sonar.conf
ADD ./docker/mysql-bindaddress.cnf /etc/mysql/conf.d/bindaddress.cnf
ADD ./docker/start.sh /start.sh
ADD ./docker/sonar.properties /opt/sonarqube/conf/sonar.properties
RUN chmod 755 /start.sh

RUN /etc/init.d/mysql start && mysql -u root --execute="create database sonar; grant all on sonar.* to sonar identified by 'sonar';"

EXPOSE 3306 9000 22

CMD ["/bin/bash", "/start.sh"]