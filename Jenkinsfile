pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Shubhamjadhavrao/tavaliing-web-site.git'
            }
        }

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
                docker run -d -p 8080:80 --name travel-web travel-web
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
