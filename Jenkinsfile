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
                    // Log in to Docker Hub using credentials in Jenkins
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-hub') {
                        // Build Docker image with the full Docker Hub tag
                        def app = docker.build("mrcyber17/devops-app:latest")
                        // Push the image to Docker Hub
                        app.push()
                    }
                }
            }
        }
    }
}
