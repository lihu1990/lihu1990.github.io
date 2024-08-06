FROM charlesjimi/centos7:centos7-arm-jdk1.8
ENV VERSION=6.8.13
MAINTAINER lihu
COPY ./elasticsearch-${VERSION}.tar.gz /usr/local
RUN cd /usr/local && tar zxvf elasticsearch-${VERSION}.tar.gz && rm -f elasticsearch-${VERSION}.tar.gz
RUN mkdir -p  /usr/share/elasticsearch/data && mkdir /usr/share/elasticsearch/log 
ADD ./elasticsearch.yml /usr/local/elasticsearch-${VERSION}/config/elasticsearch.yml
COPY ./elasticsearch-analysis-ik-${VERSION}.zip  /usr/local/elasticsearch-${VERSION}/plugins
RUN cd  /usr/local/elasticsearch-${VERSION}/plugins && unzip elasticsearch-analysis-ik-${VERSION}.zip -d analysis-ik && rm -f elasticsearch-analysis-ik-${VERSION}.zip
RUN useradd es
RUN chown -R es:es /usr/local/elasticsearch-${VERSION}/ && chown -R es:es /usr/share/elasticsearch
USER es
#WORKDIR指令用于指定容器的一个目录， 容器启动时执行的命令会在该目录下执行
WORKDIR /usr/local/elasticsearch-${VERSION}
#目录就会在运行时自动挂载为匿名卷，任何向/usr/share/elasticsearch/data中写入的信息都不会记录进容器存储层，从而保证了容器存储层的无状态化
VOLUME ["/usr/share/elasticsearch/data","/usr/share/elasticsearch/log"]
#CMD用于设置默认执行的命令
CMD ["/usr/local/elasticsearch-6.8.13/bin/elasticsearch"]
EXPOSE 9200 9300





