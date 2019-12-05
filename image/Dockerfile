ARG BASE_IMAGE=ubuntu:18.04
FROM $BASE_IMAGE
MAINTAINER Phusion <info@phusion.nl>

ARG QEMU_ARCH
ADD x86_64_qemu-${QEMU_ARCH}-static.tar.gz /usr/bin

COPY . /bd_build

RUN /bd_build/prepare.sh && \
	/bd_build/system_services.sh && \
	/bd_build/utilities.sh && \
	/bd_build/cleanup.sh

ENV DEBIAN_FRONTEND="teletype" \
    LANG="en_US.UTF-8" \
    LANGUAGE="en_US:en" \
    LC_ALL="en_US.UTF-8"

RUN apt update

#Install python3 and pip + set alias
RUN apt install -y python3 && \
    apt install -y python3-pip && \
    apt install build-essential && \

#Install data science packages
RUN pip3 install numpy -U && \
    pip3 install scipy -U && \
    pip3 install pandas -U && \
    pip3 install statsmodels -U && \
    pip3 install joblib -U && \
    pip3 install scikit-learn -U && \
    pip3 install seaborn -U &&\
    pip3 install dask -U && \
    pip3 install plotly -U && \
    pip3 install matplotlib -U && \
    pip3 install cesium -U && \
    pip3 install dtaidistance -U 

    pip3 install fbprophet -U



CMD ["/sbin/my_init"]
