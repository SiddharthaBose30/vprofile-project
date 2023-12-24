FROM openjdk:11 AS BUILD_STAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/devopshydclub/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9-jre11
LABEL project="devops"
LABEL author="siddhartha3004"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_STAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]


