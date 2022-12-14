
#!groovy
pipeline {
    agent none
}
  environment {
    DOCKERHUB_CREDENTIALS = credentials('tatianamoraru-dockerhub')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t tatianamoraru/node:16 .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push tatianamoraru/node:16'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}
