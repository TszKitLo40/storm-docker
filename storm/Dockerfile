FROM tszkitlo/base

MAINTAINER tszkitlo 
RUN wget -q https://github.com/github/git-lfs/releases/download/v1.2.0/git-lfs-linux-amd64-1.2.0.tar.gz
RUN tar -zxvf git-lfs-linux-amd64-1.2.0.tar.gz -C /opt
WORKDIR "/opt/git-lfs-1.2.0"
RUN bash install.sh
WORKDIR "/opt"
RUN mkdir storm
RUN git init
RUN git lfs track "*.tar.gz"
RUN git clone https://github.com/TszKitlo40/storm-docker /opt/storm
WORKDIR "/opt/storm"
RUN tar -zxvf apache-storm-0.11.0-SNAPSHOT.tar.gz
ENV STORM_HOME /opt/storm/apache-storm-0.11.0-SNAPSHOT
RUN groupadd storm; useradd --gid storm --home-dir /home/storm --create-home --shell /bin/bash storm; chown -R storm:storm $STORM_HOME; mkdir /var/log/storm ; chown -R storm:storm /var/log/storm

RUN ln -s $STORM_HOME/bin/storm /usr/bin/storm

ADD storm.yaml $STORM_HOME/conf/storm.yaml
ADD cluster.xml $STORM_HOME/logback/cluster.xml
ADD config-supervisord.sh /usr/bin/config-supervisord.sh
ADD start-supervisor.sh /usr/bin/start-supervisor.sh 

RUN echo [supervisord] | tee -a /etc/supervisor/supervisord.conf ; echo nodaemon=true | tee -a /etc/supervisor/supervisord.conf
