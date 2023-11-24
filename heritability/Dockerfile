FROM ubuntu:23.04

ENV PYTHONNOUSERSITE 1 
ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/Moscow
ENV gctbbin "gctb_2.05beta_scr"

RUN apt update && apt-get install -y tzdata
RUN apt install -y wget gcc g++ unzip make zlib1g-dev vim default-jre python3-pip python3-pandas  
RUN apt install libeigen3-dev libomp-dev  libboost-all-dev -y


RUN apt-get install unzip && mkdir plink && cd plink && wget -c https://s3.amazonaws.com/plink1-assets/plink_linux_x86_64_20230116.zip && unzip plink_linux_x86_64_20230116.zip && cp plink /usr/bin/plink && cd ../ && rm -rf plink && chmod +x /usr/bin/plink
# py3fastlmm

RUN export EIGEN3_INCLUDE_DIR=/usr/include/eigen3/ && export BOOST_LIB=/usr/include/boost/ && wget https://cnsgenomics.com/software/gctb/download/$gctbbin".zip" && \
    unzip $gctbbin".zip" && \
    cd $gctbbin/scr/  && make && cp gctb /usr/bin/ && cd / 
RUN apt install python3-argparse-manpage  python3-numpy python3-scipy  -y

RUN mkdir plink && cd plink && wget -c https://s3.amazonaws.com/plink1-assets/plink_linux_x86_64_20231018.zip && unzip plink_linux_x86_64_20231018.zip && cp plink /usr/bin/plink && cd ../ && rm -rf plink && chmod +x /usr/bin/plink

RUN apt install git -y
#RUN wget -c https://github.com/joepickrell/1000-genomes-genetic-maps/blob/master/scripts/interpolate_maps.py && mv  interpolate_maps.py /usr/bin/ && chmod +x /usr/bin/interpolate_maps.py
#RUN apt install build-essential gcc-10 g++-10 -y
#RUN update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-10 100 --slave /usr/bin/g++ g++ /usr/bin/g++-10 --slave /usr/bin/gcov gcov /usr/bin/gcov-10
#RUN git clone https://github.com/Soton-CompGen/LDMAP/ 
#RUN cd LDMAP && make

#RUN gcta64 -h
#RUN plink -h
