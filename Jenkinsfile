pipeline {
    agent any

    environment {
        IMAGE_NAME = "myapp"          // name for the Docker image
        CONTAINER_NAME = "myapp-container"
    }

    stages {
        stage('Checkout') {
            steps {
                // Clone source code from GitHub
                git branch: 'main', url: 'https://github.com/gowdamanu12/Jenkins-Github-Docker.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    echo "Building Docker image..."
                    sh 'docker build -t ${IMAGE_NAME}:latest .'
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    echo "Running Docker container..."
                    // Stop and remove old container if exists
                    sh """
                    docker rm -f ${CONTAINER_NAME} || true
                    docker run -d --name ${CONTAINER_NAME} -p 8080:8080 ${IMAGE_NAME}:latest
                    """
                }
            }
        }
    }

    post {
        success {
            echo '✅ Build and container run successful!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}
