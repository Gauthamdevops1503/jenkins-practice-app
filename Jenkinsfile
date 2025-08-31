pipeline {
    agent any

    environment {
        IMAGE_NAME = "jenkins-practice-app"
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out code..."
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo "Building the project..."
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests (none for now)..."
                sh 'echo "No tests yet 🚧"'
            }
        }

        stage('Docker Build') {
            steps {
                echo "Building Docker image..."
                sh "docker build -t ${IMAGE_NAME}:latest ."
            }
        }

        stage('Docker Run') {
            steps {
                echo "Running Docker container (for testing)..."
                sh "docker run -d -p 3000:3000 --name ${IMAGE_NAME}-container ${IMAGE_NAME}:latest"
            }
        }
    }

    post {
        always {
            echo "Cleaning up..."
            sh "docker rm -f ${IMAGE_NAME}-container || true"
        }
    }
}