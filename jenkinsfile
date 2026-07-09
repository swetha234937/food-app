pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'Repository cloned by Jenkins'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t food-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop food-container || true'
                sh 'docker rm food-container || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8084:80 --name food-container food-app'
            }
        }
    }
}
