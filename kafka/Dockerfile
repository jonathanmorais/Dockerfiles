FROM wurstmeister/kafka:0.11.0.1

ENV JMX_PORT 1099

RUN wget https://github.com/rhuss/jolokia/releases/download/v1.3.5/jolokia-1.3.5-bin.tar.gz && \
    tar -xvzf jolokia-1.3.5-bin.tar.gz

COPY ./start-kafka.sh  /usr/bin/
COPY ./conf/server.properties /opt/kafka/config/server.properties
RUN chmod a+x /usr/bin/start-kafka.sh

ENTRYPOINT ["start-kafka.sh"]