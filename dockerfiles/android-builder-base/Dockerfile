## Build environment for Android Open Source Project development sans Java

## from Trusted Ubuntu 14.04
FROM dockerfile/ubuntu 
MAINTAINER Tom Hiller

ENV DEBIAN_FRONTEND noninteractive

RUN \
  apt-get -qq -y update && \
  apt-get install -y file dpkg-dev ccache lzop mingw32 pngcrush nano zip && \
  apt-get install -y lib32z1-dev lib32ncurses5-dev lib32readline-gplv2-dev && \
  apt-get install -y libbz2-1.0 libbz2-dev lib32bz2-1.0 lib32bz2-dev && \
  apt-get install -y python2.7-minimal libc6-dev flex tofrodos && \
  apt-get install -y libghc-bzlib-dev libgl1-mesa-dev libncurses5-dev && \
  apt-get install -y libreadline6-dev python-markdown schedtool && \
  apt-get install -y squashfs-tools x11proto-core-dev xsltproc && \
  apt-get install -y libxml2-utils gperf bison g++-multilib zlib1g-dev && \
  apt-get install -y android-tools-adb android-tools-fastboot

## Add Repo
RUN curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > /bin/repo && \
	 chmod 755 /bin/repo

WORKDIR /root/android
VOLUME /root/android
VOLUME /root/config
VOLUME /srv/ccache

## Add ccache settings
RUN echo "source /root/config/ccache-env-vars.sh" >> /etc/bash.bashrc && \
	CCACHE_DIR=/srv/ccache ccache -M 50G

## Alias build script
RUN echo 'alias build-android="/root/config/build-android.sh"' >> /etc/bash.bashrc
