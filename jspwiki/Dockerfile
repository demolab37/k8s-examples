# FROM debian:latest
FROM tomcat:jdk17-temurin-jammy
MAINTAINER Chris Scheible<cgscheible@yahoo.com>

USER root
RUN apt-get update -y && apt-get upgrade -y
RUN curl -L -O https://dlcdn.apache.org/jspwiki/2.11.3/binaries/webapp/JSPWiki.war 

EXPOSE 8080/tcp

ENTRYPOINT ["/bin/bash"]
CMD ["-c", "/usr/local/tomcat/bin/catalina.sh run"]
