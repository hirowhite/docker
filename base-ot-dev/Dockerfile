FROM dockerfile/ubuntu

MAINTAINER Darragh Grealish "darragh@monetas.net"

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update \
	&& apt-get install -y --no-install-recommends software-properties-common \
	&& add-apt-repository ppa:hamrle/ppa \
	&& apt-get update \
	&& apt-get install -y --no-install-recommends g++ make cmake libssl-dev protobuf-compiler libprotobuf-dev libzmq3-dev git python3-dev swig3.0 cppcheck clang-format-3.5 python3-pip \
	&& ln -s /usr/bin/swig3.0 /usr/bin/swig \
	&& apt-get autoremove
ADD https://raw.githubusercontent.com/monetas/opentxs-tests/master/python3/requirements.txt /tmp/
RUN pip3 install -Ur /tmp/requirements.txt && rm /tmp/requirements.txt

RUN useradd -ms /bin/bash otuser
# set otuser home env will be used in downstream builds
ENV HOME /home/otuser
WORKDIR /home/otuser
CMD ["bash"]
