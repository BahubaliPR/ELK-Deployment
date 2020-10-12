pipeline {
    agent any 

    stages {
        stage('SCM Checkout') {
            steps {
               git credentialsId: 'Git_Cred', url: 'https://github.com/BahubaliPR/ELK-Deployment.git'
            }
        }

        stage('MVN Package') {
                def mvnHOME = tool name: 'maven3.6.3', type: 'maven'
                def mvnCMD = "${mvnHOME}/bin/mvn"
                sh "${mvnCMD} clean package"
        }
    }
       


}