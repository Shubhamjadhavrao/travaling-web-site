pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/Shubhamjadhavrao/tavaliing-web-site.git'
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
                docker rm -f travel-web || true
                docker run -d -p 8090:80 --name travel-web travel-web
                '''
            }
        }
    }

    post {
        success {
            echo "✅ Deployment Successful"
        }
        failure {
            echo "❌ Deployment Failed"
        }
    }
}
