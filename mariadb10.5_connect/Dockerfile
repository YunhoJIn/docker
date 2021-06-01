FROM ubuntu:20.04

# mysql account register
RUN groupadd -r mysql 
RUN useradd -r -g mysql mysql
RUN useradd -r -m -g mysql mha
 
# basic system install
RUN apt-get update 
RUN DEBIAN_FRONTEND="noninteractive" apt-get install -y tzdata
RUN set -ex; \
	apt-get install -y --no-install-recommends \
		sudo \
		net-tools \
		iputils-ping \
		openssh-server \
		unzip \
		wget \
		gnupg \
		dirmngr \
        curl \
        vim \ 
		locales \
		language-pack-ko \
		unixodbc \
        unixodbc-dev \
		openjdk-8-jdk \
		odbc-mariadb \
		mariadb-plugin-connect \
        software-properties-common
		
RUN curl https://mariadb.org/mariadb_release_signing_key.asc | apt-key add -
RUN echo 'deb [arch=amd64] https://ftp.harukasan.org/mariadb/repo/10.5/ubuntu focal main' >> /etc/apt/sources.list.d/mariadb.list
RUN echo 'deb-src https://ftp.harukasan.org/mariadb/repo/10.5/ubuntu focal main' >> /etc/apt/sources.list.d/mariadb.list
RUN apt-get update 

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

# set odbc driver sql server
RUN curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
RUN curl https://packages.microsoft.com/config/ubuntu/20.04/prod.list > /etc/apt/sources.list.d/mssql-release.list
RUN apt-get update
RUN ACCEPT_EULA=Y apt-get install msodbcsql17 mssql-tools
RUN echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> /etc/profile
RUN echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> /etc/bash.bashrc

# grant sudo to mysql account
RUN echo 'mysql ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers