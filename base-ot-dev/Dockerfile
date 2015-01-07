FROM dockerfile/ubuntu
#FROM ubuntu@14.04 fetched from Dockerfile Project: http://dockerfile.github.io

MAINTAINER Darragh Grealish "darragh@monetas.net"

#install the following dependencies;
RUN apt-get update \
	&& apt-get install -y --no-install-recommends software-properties-common \
	&& add-apt-repository ppa:hamrle/ppa \
	&& apt-get update \
	&& apt-get install -y --no-install-recommends g++ make cmake libssl-dev protobuf-compiler libprotobuf-dev libzmq3-dev git python3-dev swig3.0 cppcheck clang-format-3.5 python3-pip \
	&& ln -s /usr/bin/swig3.0 /usr/bin/swig \
	&& apt-get autoremove
ENV DEBIAN_FRONTEND noninteractive

RUN dpkg-reconfigure locales \
	&& locale-gen C.UTF-8 \
	&& update-locale LANG=C.UTF-8 || true 
#ENV LC_ALL C.UTF-8

# setup a non-root user
RUN useradd -ms /bin/bash otuser
# set otuser home env will be used in downstream builds
ENV HOME /home/otuser

# install test deps
ENV TEST_DIR /home/otuser/opentxs-tests
RUN mkdir -p $TEST_DIR/python3
WORKDIR $TEST_DIR/python3
RUN wget https://raw.githubusercontent.com/monetas/opentxs-tests/master/python3/requirements.txt
ENV PYTHONPATH /usr/local/lib/x86_64-linux-gnu/python3.4/site-packages/:$TEST_DIR/python3
RUN pip3 install -Ur requirements.txt

WORKDIR /home/otuser
CMD ["bash"]
