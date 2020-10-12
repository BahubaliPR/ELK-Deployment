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
                mvnHOME = tool name: 'maven3.6.3', type: 'maven'
                mvnCMD = "${mvnHOME}/bin/mvn"
                sh "${mvnCMD} clean package"
            }
        }
    }
}