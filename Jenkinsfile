pipeline {
    agent any

    environment {
        DOCKER_USERNAME = "kayalvengat"
        IMAGE_NAME = "lab-app"
    }

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/mogavengat/kubernet.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t %DOCKER_USERNAME%/%IMAGE_NAME% .'
            }
        }

        stage('Push Image') {
            steps {
                bat 'docker push %DOCKER_USERNAME%/%IMAGE_NAME%'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f deployment.yaml'
            }
        }
    }
}