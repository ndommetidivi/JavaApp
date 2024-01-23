FROM maven:3.6.3-openjdk-11 AS maven_build
WORKDIR /app/
COPY . /app/
RUN mvn -f /app/pom.xml clean package
#RUN cd target && mv loginApp.war v1.war
MAINTAINER kvurukuti@gmail.com
FROM kpogadadanda/tomcat-alpine:1
EXPOSE 8080
COPY --from=maven_build /app/target/login.war /opt/apache-tomcat-8.5.53/webapps
