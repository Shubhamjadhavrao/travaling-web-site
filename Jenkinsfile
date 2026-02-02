pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t travel-web .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker stop travel-web || true
                docker rm travel-web || true
                docker run -d -p 8082:80 --name travel-web travel-web
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Deployment Successful'
        }
        failure {
            echo '❌ Deployment Failed'
        }
    }
}
