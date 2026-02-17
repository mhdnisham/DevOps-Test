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

       stage('Django Checks') {
            steps {
                sh 'docker compose run backend python manage.py check'
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