FROM centos:6
LABEL maintainer "Andrew Leith <andrew_leith@brown.edu>"
LABEL repository compbiocore/dockerfiles
LABEL image conda-build
LABEL tag legacy

RUN yum update -y
RUN yum install -y \
  alsa-lib-devel \
  bzip2 \
  cups-devel \
  libXi-devel \
  libXrender-devel \
  libXt-devel  \
  libXtst-devel \
  java-1.7.0-openjdk-devel \
  nano \
  git \
  patch \
  redhat-lsb-core \
  sudo \
  tree \
  unzip \
  wget \
  which \
  zip

RUN yum clean all

RUN useradd -m -d /home/conda -s /bin/bash conda
RUN echo "conda ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/conda \
 && chmod 0440 /etc/sudoers.d/conda

USER conda
ENV HOME /home/conda

RUN cd /home/conda \
 && wget https://repo.continuum.io/miniconda/Miniconda2-4.5.11-Linux-x86_64.sh \
 && bash Miniconda2-4.5.11-Linux-x86_64.sh -b \
 && rm Miniconda2-4.5.11-Linux-x86_64.sh

ENV PATH /home/conda/miniconda2/bin:$PATH

RUN conda install -y conda-build=3.12.0=py27_1 anaconda-client
RUN conda clean -ay
RUN conda config --prepend channels conda-forge
RUN conda config --prepend channels compbiocore
RUN conda update -n base conda
RUN conda install -y gmp isl mpfr mpc gcc
RUN conda install -y -c conda-forge perl=5.26.2
