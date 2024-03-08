FROM openjdk:11 AS BUILD_IMAGE
RUN apt-get update && apt install maven -y
RUN git clone https://github.com/surajsb007/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9-jre11
LABEL "PRJ"="VPROFILE"
LABEL "NAME"="SB"
RUN rm -rf /usr/local/tomcat/webaps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war //usr/local/tomcat/webaps/ROOT.war


EXPOSE 8080
CMD ["catalina.sh", "run"]