FROM maven:3.9-amazoncorretto-17-debian

USER root
WORKDIR /opt
COPY . /opt
#RUN mvn verify clean --fail-never
#RUN ./mvnw package
RUN apt update && apt-get install -y libc6
RUN mvn clean install -DskipTests

EXPOSE 8080

CMD ["java", "-javaagent:/opt/RASP/imperva-agent-4.4.1.jar", "-Dimperva.config=/opt/RASP/imperva-4.4.0-testami-e-cancellami.json", "-Dimperva.raspjarpath=/opt/RASP/imperva-rasp-4.4.1.jar", "-Dspring.profiles.active=mysql", "-jar", "target/spring-petclinic-3.2.0-SNAPSHOT.jar"]