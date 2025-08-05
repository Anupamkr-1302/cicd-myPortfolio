pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        echo '🔨 Building Docker image...'
        sh 'docker build -t anupam-portfolio .'
      }
    }

    stage('Test') {
      steps {
        echo '🔍 Testing container...'
        sh 'docker run -d -p 8082:80 --name test-container anupam-portfolio'
        sh 'sleep 5'
        sh 'curl -I http://localhost:8082'
        sh 'docker stop test-container && docker rm test-container'
      }
    }

    stage('Deploy') {
      steps {
        echo '🚀 Deploying...'
        sh 'docker stop live-portfolio || true'
        sh 'docker rm live-portfolio || true'
        sh 'docker run -d -p 8080:80 --name live-portfolio anupam-portfolio'
      }
    }
  }
}
