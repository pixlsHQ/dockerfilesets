#
# MongoDB Dockerfile
#
# https://github.com/dockerfile/mongodb
#

# Pull base image.
FROM ubuntu:12.04
MAINTAINER William Li, williamli@quriousone.io

# Install MongoDB.
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
RUN echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | tee /etc/apt/sources.list.d/mongodb.list
RUN dpkg-divert --local --rename --add /sbin/initctl
RUN ln -fs /bin/true /sbin/initctl
RUN apt-get update
RUN apt-get install -y mongodb-10gen

# Install VIM
RUN apt-get install -y vim

# Create default MongoDB data directory.
#RUN mkdir -p /data/db

# Expose ports.
#   - 27017: process
#   - 28017: http
EXPOSE 27017
EXPOSE 28017

# Define an entry point.
ENTRYPOINT ["mongod", "-f", "/oxygen/mongodb/mongodb.conf"]

# starts with docker run -name mongodb -v /var/dockerstore/oxygen/mongodb:/oxygen/mongodb -d -p 27017:27017 oxygen/mongodb
