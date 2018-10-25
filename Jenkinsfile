pipeline {
  agent {
    docker {
      image 'node:8.9-alpine'
    }

  }
  stages {
    stage('confgs') {
      steps {
        sh 'ls -l -a'
        dir(path: 'backend/') {
          sh '''yarn install
'''
        }

      }
    }
    stage('check') {
      steps {
        sh 'ls -l -a'
        sh 'yarn check'
      }
    }
    stage('build') {
      steps {
        sh 'ls -l -a'
        sh 'yarn build'
      }
    }
  }
}