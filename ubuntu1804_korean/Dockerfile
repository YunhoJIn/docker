FROM ubuntu:18.04
 
# basic system install
RUN apt-get update 
RUN DEBIAN_FRONTEND="noninteractive" apt-get install -y tzdata
RUN set -ex; \
	apt-get install -y --no-install-recommends \
		sudo \
		net-tools \
		iputils-ping \
		wget \
		gnupg \
		dirmngr \		
        curl \
        vim \ 
		locales \
		language-pack-ko \
        software-properties-common

# set to language korean
RUN	locale-gen ko_KR.UTF-8
ENV LC_ALL C.UTF-8
ENV LANGUAGE ko_KR.UTF-8
ENV LANG ko_KR.UTF-8
RUN update-locale LANG=ko_KR.UTF-8 LC_MESSAGES=POSIX

# set environment variable
ENV TZ=Asia/Seoul
ENV TERM=xterm-256color
ENV NLS_LANG=KOREAN_KOREA.AL32UTF8