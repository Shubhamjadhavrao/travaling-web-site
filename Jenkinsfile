pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
              git branch: 'main',
                  git 'https://github.com/Shubhamjadhavrao/travaling-web-site.git'
            }
        }

        stage('Build Image') {
            steps {
                sh '''
                eval $(minikube docker-env)
                docker build -t travel-web .
                '''
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                kubectl apply -f ./minikube/deployment.yml
                kubectl apply -f ./minikube/service.yml
                '''
            }
        }
    }
}
