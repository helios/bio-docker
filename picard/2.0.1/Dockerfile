# INGM Bioinformatics
#
# DESCRIPTION DeNovoHuman Installation of Picard
# VERSION             2.0.1
# CREATION 2016-02-05

FROM      ubuntu:14.04
MAINTAINER Raoul J.P. Bonnal <ilpuccio.febo@gmail.com>

RUN apt-get update --fix-missing && apt-get install -y wget build-essential lib32z1-dev software-properties-common python unzip


# Install Java 8
# source https://github.com/dockerfile/java/blob/master/oracle-java8/Dockerfile
RUN \
  echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections && \
  add-apt-repository -y ppa:webupd8team/java && \
  apt-get update && \
  apt-get install -y oracle-java8-installer && \
  rm -rf /var/lib/apt/lists/* && \
  rm -rf /var/cache/oracle-jdk8-installer


RUN cd /opt &&\
    wget "https://github.com/broadinstitute/picard/releases/download/2.0.1/picard-tools-2.0.1.zip" && \
    unzip picard-tools-2.0.1.zip

ADD stub.sh /opt/picard-tools-2.0.1/

RUN cd /opt/picard-tools-2.0.1 && \
    cat stub.sh picard.jar > picard && \
    chmod 755 picard

ENV PATH /opt/picard-tools-2.0.1:$PATH

# Define commonly used JAVA_HOME variable
ENV JAVA_HOME /usr/lib/jvm/java-8-oracle

#COPY entrypoint.sh /sbin/entrypoint.sh
#RUN chmod 755 /sbin/entrypoint.sh

#RUN echo 'PATH=/opt/cufflinks-2.2.1.Linux_x86_64/:$PATH' >> /root/.bashrc
#RUN echo 'PATH=/opt/cufflinks-2.2.1.Linux_x86_64/:$PATH' >> /root/.profile

#COPY README.md /README.md

#ENTRYPOINT ["/sbin/entrypoint.sh"]
