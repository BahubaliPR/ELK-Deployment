#using alpine base image
FROM openjdk:8-jre-alpine

ADD /var/lib/jenkins/workspace/My-CICD-Project/SpringBoot-App/target/SpringBootApp.war ./SpringBoot-App.war

EXPOSE 8080

ENTRYPOINT ["java","-jar","./SpringBootApp.war"]