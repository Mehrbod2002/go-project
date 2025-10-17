pipeline {
    agent any
    environment {
        DOCKER_IMAGE = "mehrbodw/go-jenkins-app:latest" 
        PATH = "/usr/local/bin:$PATH"
    }
    stages {
        stage('Build') {
            steps {
                script {
                    sh 'docker build -t $DOCKER_IMAGE .'
                }
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                script {
                    sh 'kubectl apply -f k8s/deployment.yaml'
                }
            }
        }
    }
}