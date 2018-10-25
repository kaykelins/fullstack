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
      parallel {
        stage('build') {
          steps {
            dir(path: 'backend/') {
              timeout(time: 1, activity: true) {
                sh '''yarn build
'''
              }

            }

          }
        }
        stage('') {
          steps {
            sh 'curl localhost:3000'
          }
        }
      }
    }
  }
}