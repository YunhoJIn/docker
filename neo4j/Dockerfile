FROM neo4j:latest

# basic system install
RUN apt-get update 
RUN DEBIAN_FRONTEND="noninteractive" apt-get install -y tzdata
RUN set -ex; \
	apt-get install -y --no-install-recommends \
		procps \
		sudo \
		net-tools \
		iputils-ping \
		wget \
		gnupg \
		dirmngr \		
        curl \
        vim \ 
		locales \
		locales-all \
        software-properties-common

# set to language korean
ENV LC_ALL C.UTF-8
ENV LANGUAGE ko_KR.UTF-8
ENV LANG ko_KR.UTF-8
ENV LC_TYPE ko_KR.UTF-8
RUN	locale-gen ko_KR.UTF-8
RUN update-locale LANG=ko_KR.UTF-8 LC_MESSAGES=POSIX

# set environment variable
ENV TZ=Asia/Seoul
ENV TERM=xterm-256color

WORKDIR /home/neo4j