pipeline {
    agent any 
    stages {
        stage('SCM Checkout') {
            steps {
               git credentialsId: 'Git_Cred', url: 'https://github.com/BahubaliPR/ELK-Deployment.git'
            }
        }

        stage('MVN Package') {
            steps {
                    sh 'cd /var/lib/jenkins/workspace/My-CICD-Project/SpringBoot-App/'
                    sh '/usr/share/maven/bin/mvn clean package'             
            }
        }
    }
}