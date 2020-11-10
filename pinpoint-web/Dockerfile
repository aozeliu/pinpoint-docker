FROM tomcat:8-jre8

LABEL maintainer="Roy Kim <roy.kim@navercorp.com>"

ARG PINPOINT_VERSION=${PINPOINT_VERSION:-1.8.5}
ARG INSTALL_URL=https://github.com/naver/pinpoint/releases/download/${PINPOINT_VERSION}/pinpoint-web-${PINPOINT_VERSION}.war

COPY pinpoint-web-1.8.6-SNAPSHOT.war pinpoint-web.war
COPY /build/scripts/start-web.sh /usr/local/bin/
COPY /build/mail.zip /assets/mail.zip
COPY /build/javax.mail-1.5.2.jar javax.mail-1.5.2.jar

RUN chmod a+x /usr/local/bin/start-web.sh \
    && rm -rf /usr/local/tomcat/webapps \
    && mkdir -p /usr/local/tomcat/webapps \
    && unzip pinpoint-web.war -d /usr/local/tomcat/webapps/ROOT \
    && rm -rf pinpoint-web.war \
    && cp javax.mail-1.5.2.jar /usr/local/tomcat/webapps/ROOT/WEB-INF/lib/javax.mail-1.5.2.jar \
    && rm -rf javax.mail-1.5.2.jar \
    && unzip /assets/mail.zip -d /usr/local/tomcat/webapps/ROOT/WEB-INF/classes/ \
    && rm -rf /assets/mail.zip

# COPY /webrts-collector-1.0-jar-with-dependencies.jar webrts-collector-1.0.jar
# RUN cp -f webrts-collector-1.0.jar /usr/local/tomcat/webapps/ROOT/WEB-INF/lib/ \
#     && rm webrts-collector-1.0.jar

# COPY /jpetstoreplugin-1.8.4.jar jpetstoreplugin-1.8.4.jar
# RUN cp -f jpetstoreplugin-1.8.4.jar /usr/local/tomcat/webapps/ROOT/WEB-INF/lib/ \
#     && rm jpetstoreplugin-1.8.4.jar

ENTRYPOINT ["/usr/local/bin/start-web.sh"]
