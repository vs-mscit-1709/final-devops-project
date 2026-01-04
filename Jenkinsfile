pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/vs-mscit-1709/final-devops-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("mrcyber17/devops-app")
                }
            }
        }

        stage('Push Image to Docker Hub') {
            steps {
                withDockerRegistry([credentialsId: 'docker-hub']) {
                    docker.image("mrcyber17/devops-app").push("latest")
                }
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 3000:3000 mrcyber17/devops-app'
            }
        }
    }
}
