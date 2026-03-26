pipeline {
    agent any
    
    stages{
        stage('Clone repo') {
            steps{
                 git branch: 'main', url: 'https://github.com/muddasir-x/devops-project.git'
            }
        }
        
        stage('Build backend image') {
            steps {
                sh 'docker build -t my-backend:v2 backend/'
            }
        }
        
        stage('Build frontend image') {
            steps{
                sh 'docker build -t my-frontend:v2 frontend/'
            }
        }
        
        stage('Skip Kind Load') {
            steps {
                echo "Skipping kind load"
            }
        }
        
        stage('Deploy kubernetes') {
            steps{
                sh 'kubectl apply -f k8s/'
            }
        }
    }
}
