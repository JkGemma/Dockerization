FROM debian:buster-slim
MAINTAINER quentin.flayac@epitech.eu - q.flayac@upfactor.fr

RUN apt-get update \
  && apt-get install -y --no-install-recommends \
  automake \
  cmake \
  ca-certificates \
  # build-essential \
  g++ \
  liblz4-dev \
  libeigen3-dev \
  libopencv-dev \
  python3-opencv \
  libpcl-dev \
  wget \
  git

WORKDIR /
RUN git clone https://github.com/tudelft3d/masbcpp.git \
 && cd masbcpp \
 && cmake . \
 && make
