pipeline {
    agent any
    environment {
        DOCKER_IMAGE = "go-jenkins-app:latest"
        K8S_DEPLOY_FILE = "k8s/deployment.yaml"
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
                    sh 'kubectl apply -f $K8S_DEPLOY_FILE'
                }
            }
        }
    }
}