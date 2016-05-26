FROM tszkitlo/base

MAINTAINER tszkitlo

RUN wget -q http://download.nus.edu.sg/mirror/apache/zookeeper/zookeeper-3.4.8/zookeeper-3.4.8.tar.gz 
RUN tar -zxvf zookeeper-3.4.8.tar.gz -C /opt
RUN mv /opt/zookeeper-3.4.8/conf/zoo_sample.cfg /opt/zookeeper-3.4.8/conf/zoo.cfg

ENV JAVA_HOME /usr/lib/jvm/java-7-openjdk-amd64
ENV ZK_HOME /opt/zookeeper-3.4.8
RUN sed  -i "s|/tmp/zookeeper|$ZK_HOME/data|g" $ZK_HOME/conf/zoo.cfg; mkdir $ZK_HOME/data

ADD start-zk.sh /usr/bin/start-zk.sh 
EXPOSE 2181 2888 3888

WORKDIR /opt/zookeeper-3.4.8
VOLUME ["/opt/zookeeper-3.4.8/conf", "/opt/zookeeper-3.4.8/data"]

CMD /usr/sbin/sshd && bash /usr/bin/start-zk.sh

