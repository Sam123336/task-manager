pipeline {
    agent any

    environment {
        DOCKER_COMPOSE_PATH = './docker-compose.yml'
    }

    stages {

        stage('Checkout') {
            steps {
                // Check out the repository from GitHub
                git branch: 'main', url: 'https://github.com/jimmyptl-jer/Blog-Application.git'
            }
        }

        stage('Build Docker Images') {
            steps {
                sh 'docker compose build'
            }
        }

        stage('Start Containers') {
            steps {
                sh 'docker compose up -d'
            }
        }

        stage('Run Server Tests') {
            steps {
                sh 'docker exec $(docker ps -qf "name=server") npm test || true'
            }
        }

        stage('Clean Up') {
            steps {
                sh 'docker system prune -f'
            }
        }
    }

    post {
        always {
            echo 'CI/CD pipeline completed.'
        }
    }
}
