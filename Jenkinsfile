pipeline {
    agent any
    environment {
        DOCKER_IMAGE = "go-jenkins-app"
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
        stage('Push to Docker Registry') {
            steps {
                script {
                    sh 'docker push $DOCKER_IMAGE'
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
