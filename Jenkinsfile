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
                      docker build -t Bahubalipr/springapp:1.5.14 ./SpringBoot-App/.
                     """
                }
                     
               } 
            }
        
        stage('Docker Push') {
            steps {
                   withCredentials([string(credentialsId: 'DOCKER_HUB_CREDENTIALS', variable: 'DOCKER_HUB_CREDENTIALS')]) {
                   sh "docker login -u Bahubalipr -p ${DOCKER_HUB_CREDENTIALS}"
            }
                script {
                    sh """
                      docker push bahubalipr/springapp:1.5.14
                    """
             }
        }
    }
        
        // stage('Deploy in Kubernetes') {
        //     steps {
        //         script {
        //             sh """
        //             kubectl create -f Deploy.yaml
        //             """
        //         }
        //     }
        //  }


        }
    }