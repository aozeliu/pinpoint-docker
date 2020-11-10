FROM ismaleiva90/weblogic12:latest

LABEL maintainer="azl"

COPY /jpetstore.war /u01/oracle/weblogic/user_projects/domains/base_domain/servers/AdminServer/upload/jpetstore.war
COPY /config.xml /u01/oracle/weblogic/user_projects/domains/base_domain/config/config.xml
# RUN rm -rf /usr/local/tomcat/webapps \
#     && mkdir -p /usr/local/tomcat/webapps \
#     && unzip quickstart.war -d /usr/local/tomcat/webapps/ROOT \
#     && rm -rf quickstart.war

# COPY /build/jpetstore-1.0.war /usr/local/tomcat/webapps/jpetstore-1.0.war
# COPY /build/simple-1.0.war /usr/local/tomcat/webapps/simple-1.0.war

CMD [ "/u01/oracle/weblogic/user_projects/domains/base_domain//bin/startWebLogic.sh"]
