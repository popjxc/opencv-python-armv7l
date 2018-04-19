FROM registry.cn-beijing.aliyuncs.com/h2c-arm/debian-python

RUN [ "cross-build-start" ]

# install opencv & hostapd
RUN  apt-get update && apt-get install -y --no-install-recommends \
        cmake \
        isc-dhcp-server \
        autoconf automake libtool pkg-config \
        git 
RUN git clone https://github.com/skvark/opencv-python
WORKDIR opencv-python
RUN git submodule update --init --recursive
RUN python3 find_version.py
RUN pip install numpy==1.11.3
RUN apt-get install build-essential qt4-default
RUN echo "python3 setup.py build" >> ./run.sh
RUN echo "exit 0" >> ./run.sh
RUN /bin/bash ./run.sh
#RUN python3 setup.py install


RUN [ "cross-build-end" ]
