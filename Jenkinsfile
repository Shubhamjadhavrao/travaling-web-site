pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Shubhamjadhavrao/travaling-web-site.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t travel-web .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop travel-web || true
                docker rm travel-web || true
                docker run -d -p 8082:80 --name travel-web travel-web
                '''
            }
        }
    }
}
