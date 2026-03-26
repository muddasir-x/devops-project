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
                sh 'docker build -t my-backend:v2 .'
            }
        }
        
        stage('Build frontend image') {
            steps{
                sh 'docker build -t my-frontend:v2 .'
            }
        }
        
        stage('load image to kubernetes') {
            steps {
                sh 'kind load docker-image my-backend:v2 --name dev-cluster'
                sh 'kind load docker-image my-frontend:v2 --name dev-cluster'
            }
        }
        
        stage('Deploy kubernetes') {
            steps{
                sh 'kubectl apply -f k8s/'
            }
        }
    }
}
