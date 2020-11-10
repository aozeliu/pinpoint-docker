FROM java:8-jdk

LABEL maintainer="azl"

COPY /mybatis-spring-boot-jpetstore-2.0.0-SNAPSHOT.jar /opt/quickstart/jpetstore.jar

WORKDIR /opt/quickstart/

ENTRYPOINT java ${JAVA_OPTS} -jar /opt/quickstart/jpetstore.jar
