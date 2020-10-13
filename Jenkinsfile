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
                        docker build -t bahubalipr/springapp:1.5.14 ./SpringBoot-App/.
                     """
                }
                     
               } 
            }
        
        stage('Docker Push') {
            steps {
                   withCredentials([string(credentialsId: 'DOCKER_HUB_CRED', variable: 'DOCKER_HUB_CRED')]) {
                   sh "docker login -u bahubalipr -p ${DOCKER_HUB_CRED}"
            }
                script {
                    sh """
                      docker push bahubalipr/springapp:1.5.14
                    """
             }
        }
    }
        
        stage('Deploy application in K8S') {
            steps {
                kubernetesDeploy configs: 'kubectl create -f **/SpringBoot-App/*.yaml', kubeconfigId: 'KUBERNETES_CONFIG'
            }
         }


        }
    }