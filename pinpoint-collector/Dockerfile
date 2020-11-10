FROM tomcat:8-jre8

LABEL maintainer="Roy Kim <roy.kim@navercorp.com>"

ARG PINPOINT_VERSION=${PINPOINT_VERSION:-1.8.5}

ARG INSTALL_URL=https://github.com/naver/pinpoint/releases/download/${PINPOINT_VERSION}/pinpoint-collector-${PINPOINT_VERSION}.war

COPY pinpoint-collector-${PINPOINT_VERSION}.war pinpoint-collector.war
COPY /build/scripts/start-collector.sh /usr/local/bin/

RUN chmod a+x /usr/local/bin/start-collector.sh \
    && rm -rf /usr/local/tomcat/webapps \
    && mkdir -p /usr/local/tomcat/webapps \
    && unzip pinpoint-collector.war -d /usr/local/tomcat/webapps/ROOT \
    && rm -rf pinpoint-collector.war \
    && sed -i "s/8005/9005/g" /usr/local/tomcat/conf/server.xml \
    && sed -i "s/8080/9080/g" /usr/local/tomcat/conf/server.xml \
    && sed -i "s/8009/9009/g" /usr/local/tomcat/conf/server.xml \
    && sed -i "s/8443/9443/g" /usr/local/tomcat/conf/server.xml

# COPY /webrts-collector-1.0-jar-with-dependencies.jar webrts-collector-1.0.jar
# RUN cp -f webrts-collector-1.0.jar /usr/local/tomcat/webapps/ROOT/WEB-INF/lib/ \
#     && rm webrts-collector-1.0.jar

# COPY /jpetstoreplugin-1.8.4.jar jpetstoreplugin-1.8.4.jar
# RUN cp -f jpetstoreplugin-1.8.4.jar /usr/local/tomcat/webapps/ROOT/WEB-INF/lib/ \
#     && rm jpetstoreplugin-1.8.4.jar

ENTRYPOINT ["/usr/local/bin/start-collector.sh"]

