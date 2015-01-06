FROM ubuntu:14.04

MAINTAINER Darragh Grealish "darragh@monetas.net"

WORKDIR /home/otbuilder/

#install the following dependencies;
RUN set +x; \
                apt-get update \
                && apt-get install -y --no-install-recommends software-properties-common \
                && add-apt-repository ppa:hamrle/ppa \
                && apt-get update \
                && apt-get install -y --no-install-recommends g++ make cmake libssl-dev protobuf-compiler libprotobuf-dev libzmq3-dev git python3-dev swig3.0 cppcheck clang-format-3.5 \
                && ln -s /usr/bin/swig3.0 /usr/bin/swig \
                && apt-get autoremove
ENV DEBIAN_FRONTEND noninteractive
RUN set +x; \
                dpkg-reconfigure locales \
                && locale-gen C.UTF-8 \
                && update-locale LANG=C.UTF-8 || true 
#ENV LC_ALL C.UTF-8

# setup a non-root user
RUN useradd -ms /bin/bash otuser
# become otuser and create build folder but check if it already exists 
USER otuser
ENV HOME /home/otuser
WORKDIR /home/otuser

RUN set +x; \
                cd ~/ \
                && mkdir opentxs-source \
                && cd opentxs-source \
                && mkdir build
USER root
CMD /bin/bash/
