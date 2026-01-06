pipeline {
    agent any  // Runs the pipeline on any available Jenkins agent

    environment {
        IMAGE_NAME = "myapp:latest" // Docker image name
    }

    stages {

        stage('Pull Code from GitHub') {
            steps {
                git branch: 'main', url: 'https://github.com/yourusername/your-repo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${env.IMAGE_NAME}")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Stop existing container if running
                    sh "docker rm -f myapp-container || true"
                    // Run new container
                    sh "docker run -d --name myapp-container -p 8080:80 ${env.IMAGE_NAME}"
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline finished."
        }
    }
}
