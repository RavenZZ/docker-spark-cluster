FROM centos:7

MAINTAINER RavenZZ <raven.zhu@outlook.com>


# Copy shell files
COPY wait-for-step.sh /
COPY execute-step.sh /
COPY finish-step.sh /


# Install system tools
RUN yum update -y
RUN yum upgrade -y
RUN yum install -y byobu curl htop man unzip nano wget
RUN yum clean all

# Install Java
ENV JDK_VERSION 8u11
ENV JDK_BUILD_VERSION b12
#RUN curl -LO "http://download.oracle.com/otn-pub/java/jdk/$JDK_VERSION-$JDK_BUILD_VERSION/jdk-$JDK_VERSION-linux-x64.rpm" -H 'Cookie: oraclelicense=accept-securebackup-cookie' && rpm -i jdk-$JDK_VERSION-linux-x64.rpm; rm -f jdk-$JDK_VERSION-linux-x64.rpm;
RUN curl -LO "http://172.17.10.164:54321/jdk-8u11-linux-x64.rpm" && rpm -i jdk-$JDK_VERSION-linux-x64.rpm; rm -f jdk-$JDK_VERSION-linux-x64.rpm;
ENV JAVA_HOME /usr/java/default
RUN yum remove curl;  yum clean all

# RUN apt-get install git

# ARG SPARK_VERSION="branch-2.1"

# RUN git clone  --depth 1 --branch ${SPARK_VERSION} https://github.com/apache/spark.git

WORKDIR spark


RUN \
    curl -LO 'http://172.17.10.164:54321/spark-2.1.0-bin-hadoop2.7.tgz' && \
    tar zxf spark-2.1.0-bin-hadoop2.7.tgz

RUN rm -rf spark-2.1.0-bin-hadoop2.7.tgz
RUN mv spark-2.1.0-bin-hadoop2.7/* ./

# ENV R_HOME /usr/lib/R
# RUN ./R/install-dev.sh

# ENV MAVEN_OPTS "-Xmx2g -XX:ReservedCodeCacheSize=512m"
# ARG MAJOR_HADOOP_VERSION="2.7"
# RUN ./build/mvn -Pyarn -Pmesos -Phive  -Psparkr  -Phive-thriftserver -Phadoop-${MAJOR_HADOOP_VERSION} -Dhadoop.version=${MAJOR_HADOOP_VERSION}.0 -DskipTests clean package

ENV SPARK_HOME /spark
ENV PATH /spark/bin:$PATH
ENV PATH /spark/sbin:$PATH






