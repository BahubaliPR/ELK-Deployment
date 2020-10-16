#using alpine base image
FROM openjdk:8-jre-alpine

#WORKDIR /var/lib/jenkins/workspace/My-CICD-Project/SpringBoot-App/target/
ADD ./target/SpringBootApp.war ./SpringBoot-App.war

EXPOSE 8080

ENTRYPOINT ["java","-jar","./SpringBootApp.war"]