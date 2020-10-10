pipeline {
    agent any 
    tools {
        terraform 'terraform0.13.2'
    }
    
    stages {
        stage('Git Checkout') {
            steps {
               git credentialsId: 'Git_Cred', url: 'https://github.com/BahubaliPR/ELK-Deployment.git'
            }
        }

        stage ('Terraform Init') {
            steps {
               sh 'terraform init'
            }
        }

        stage ('Terraform Apply') {
            steps {
               sh 'terraform apply --auto-approve'
            }
        }
    }
}