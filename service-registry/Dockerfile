FROM openjdk:8
RUN apt-get update && apt-get -y install netcat && apt-get clean
ADD ["target/service-registry-0.0.1-SNAPSHOT-exec.jar", "app.jar"]
EXPOSE 8761 8787
ENV JAVA_OPTS="-Xdebug -Xrunjdwp:server=y,transport=dt_socket,address=8787,suspend=n"
RUN sh -c 'touch /app.jar'
ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -Dspring.profiles.active=docker -jar /app.jar" ]
