FROM openjdk:11 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/adhicodes/vprofile-project2.git
RUN cd vprofile-project2 && git checkout docker && mvn install

FROM tomcat:9-jre11
LABEL "Author"="Adhitya"
LABEL "Project"="vprofile"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project2/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
