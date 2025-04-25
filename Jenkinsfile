pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                // Check out the repository from GitHub
                git branch: 'main', url: 'https://github.com/Sam123336/task-manager.git'
            }
        }

        stage('Build Docker Images') {
            steps {
                // Build using docker-compose.yml at the root of the workspace
                sh 'docker compose build'
            }
        }

        stage('Start Containers') {
            steps {
                // Start containers using docker-compose
                sh 'docker compose up -d'
            }
        }

        stage('Run Server Tests') {
            steps {
                // Run tests in the container named 'server' or matching
                sh 'docker exec $(docker ps -qf "name=server") npm test || true'
            }
        }

        stage('Clean Up') {
            steps {
                // Remove unused Docker resources
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
