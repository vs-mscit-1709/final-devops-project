pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/vs-mscit-1709/final-devops-project.git'
            }
        }

        stage('Build & Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-hub') {
                        // Build Docker image from repo root
                        def app = docker.build("mrcyber17/devops-app:latest")
                        // Push image to Docker Hub
                        app.push()
                    }
                }
            }
        }
    }
}
