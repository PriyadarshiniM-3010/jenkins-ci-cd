pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t my-app .'
      }
    }

    stage('Test') {
      steps {
        sh 'echo "Testing app..."'
      }
    }

    stage('Deploy') {
      steps {
        sh '''
          docker rm -f my-app-container || true
          docker run -d -p 8082:3000 --name my-app-container my-app
        '''
      }
    }
  }
}
