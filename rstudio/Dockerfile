FROM rocker/rstudio:latest
MAINTAINER Andrew Leith "andrew_leith@brown.edu"

RUN apt-get install -y \
	pkg-config \
	libxml2 \
	libstdc++6 \
	libz-dev \
	libglpk-dev

RUN apt-get clean all

