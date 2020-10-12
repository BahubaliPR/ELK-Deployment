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
                script {
                    sh """
                     cd /var/lib/jenkins/workspace/My-CICD-Project/SpringBoot-App
                     /usr/share/maven/bin/mvn clean package
                    """   
                }                              
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh """
                      springAppImage=docker images springapp:1.5.14
                      if [ $springAppImage -eq springapp:1.5.14 ]
                      then
                         echo "The image is already exists."
                      else
                         docker build -t springapp:1.5.14 ./SpringBoot-App/.
                     """
                }
                     
               } 
            }
        
        stage('Deploy in Kubernetes') {
            steps {
                script {
                    sh """
                    kubectl apply -f ./Deploy.yaml
                    """
                }
            }
        }
        }
    }