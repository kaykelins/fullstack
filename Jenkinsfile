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
        dir(path: 'backend/') {
          sh 'yarn check'
          sh 'ls -l -a'
        }

      }
    }
    stage('build') {
      steps {
        dir(path: 'backend/') {
          timeout(time: 2, activity: true) {
            sh 'yarn build'
            echo 'works'
          }

        }

      }
    }
  }
}