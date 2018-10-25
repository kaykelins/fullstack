pipeline {
  agent {
    docker {
      image 'node:8.9-alpine'
    }

  }
  stages {
    stage('confgs') {
      steps {
        sh '''yarn install
'''
      }
    }
    stage('check') {
      steps {
        sh 'yarn check'
      }
    }
    stage('build') {
      steps {
        sh 'yarn build'
      }
    }
  }
}