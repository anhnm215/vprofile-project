# We need mvn command to build the artifact, for maven we need JDK
FROM openjdk:11 AS BUILD_IMAGE
# we already have jdk, we need maven
# This jdk image is based on Debian -> use apt command
# can see that info in the image doc on Docker Hub
RUN apt update && apt install maven -y
# clone the source code, checkout to the branch docker and run 'mvn install'
# this will generate the artifact vprofile-v2.war in vprofile-project/target
RUN git clone https://github.com/devopshydclub/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9-jre11
LABEL "Project"="Vprofile"
LABEL "Author"="anhnm"
# remove the default artifact
# can find out the default tomcat app location in tomcat image documentation in Docker hub
# In real time, you get the information how to run the application locally from the dev, based on that information, you put write the Dockerfile
RUN rm -rf /usr/local/tomcat/webapps/*
# copy the artifact that was created in the first stage into webapps folder with the name ROOT.war
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
# this is enough, tomcat will run the process on port 8080

# the tomcat base image runs the process on port 8080 and it's already exposed
# just add extra instruction (not required)
EXPOSE 8080
# CMD - the command to run is also already decided in tomcat base image by default
# we don't need to give it
CMD ["catalina.sh", "run"]
# /usr/local/tomcat is the work dir where you have catalina.sh (see tomcat image doc)
# you can give more instruction: WORKDIR, VOLUME,... but this is enough
