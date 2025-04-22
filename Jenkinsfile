pipeline {
    agent any

    environment {
        IMAGE_NAME = "voting-app"
        TAG = "latest"
    }

    stages {
        stage('Clone Repository') {
            steps {
                echo "Cloning repository..."
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "Building Docker image..."
                script {
                    docker.build("${IMAGE_NAME}:${TAG}")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                echo "Running Docker container..."
                script {
                    docker.run("-d -p 3000:3000 --name ${IMAGE_NAME} ${IMAGE_NAME}:${TAG}")
                }
            }
        }
    }
}
