FROM ubuntu:16.04
LABEL maintainer "Mark Howison <mhowison@brown.edu>"
LABEL repository compbiocore
LABEL image albacore
LABEL tag 1.2.5-1

RUN apt-get -y update
RUN apt-get -y install wget
RUN wget -O- https://mirror.oxfordnanoportal.com/apt/ont-repo.pub | apt-key add -
RUN echo "deb http://mirror.oxfordnanoportal.com/apt trusty-stable non-free" | tee /etc/apt/sources.list.d/nanoporetech.sources.list
RUN apt-get -y update
RUN dpkg -i python3-ont-albacore_1.2.5-1~xenial_all.deb
RUN apt-get -yf install
RUN apt-get -y autoremove
RUN aptitude clean
RUN aptitude autoclean
