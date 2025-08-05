pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo '🔨 Building Docker image...'
                sh 'docker build -t my-portfolio .'
            }
        }

        stage('Test') {
            steps {
                echo '🔍 Testing container...'
                // Use host network to allow Jenkins to reach the app
                sh 'docker run -d --network host --name test-container my-portfolio'
                sh 'sleep 5'
                sh 'curl -I http://localhost:80'
                sh 'docker stop test-container || true'
                sh 'docker rm test-container || true'
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Deploy stage (placeholder)...'
                // You can add deployment commands here later
            }
        }
    }
}
