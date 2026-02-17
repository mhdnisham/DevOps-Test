pipeline {
    agent any

    environment {
        COMPOSE_FILE = 'docker-compose.yml'
    }

    stages {

        stage('Checkout Code') {
            steps {
                echo "Cloning repository..."
                git branch: 'main',
                    url: 'https://github.com/mhdnisham/DevOps-Test.git'
            }
        }

        stage('Stop Old Containers') {
            steps {
                echo "Stopping existing containers..."
                sh 'docker compose down || true'
            }
        }

  stage('Build Docker Images') {
            steps {
                sh 'docker compose build'
            }
        }

        stage('Run Containers') {
            steps {
                sh 'docker compose up'
            }
        }

    }
}