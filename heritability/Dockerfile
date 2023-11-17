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
    cd $gctbbin/scr/  && make && cp gctb /usr/bin/ && cd / \
    rm -rf $gctbbin*
#RUN pip3 install argparse numpy
#ENV PATH="/usr/lib/plink/:${PATH}"


#RUN gcta64 -h
#RUN plink -h
