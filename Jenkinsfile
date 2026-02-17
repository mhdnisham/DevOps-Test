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
                echo "Building Docker images..."
                sh 'docker compose build'
            }
        }

        stage('Run Containers') {
            steps {
                echo "Starting containers..."
                sh 'docker compose up -d'
            }
        }

        stage('Run Migrations') {
            steps {
                echo "Running Django migrations..."
                sh 'docker compose exec backend python manage.py migrate || true'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully 🚀'
        }
        failure {
            echo 'Pipeline failed ❌'
        }
        always {
            echo 'Build finished.'
        }
    }
}
