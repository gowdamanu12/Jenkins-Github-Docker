pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/gowdamanu12/ultimate-devops-project-demo.git'
            }
        }

        stage('List Files') {
            steps {
                sh 'echo "Listing project files:"'
                sh 'ls -R'
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Build stage executed successfully!"'
            }
        }
    }
}
