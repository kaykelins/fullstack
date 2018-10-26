pipeline {
  agent {
    docker {
      image 'node:8.9-alpine'
    }

  }
  stages {
    stage('confgs') {
      steps {
        dir(path: 'backend/') {
          sh 'ls -l -a'
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
            catchError() {
              dir(path: 'backend/') {
                sh 'yarn build'
              }

            }

          }
        }
        stage('error') {
          steps {
            sh 'netstat -l | egrep 3000'
          }
        }
      }
    }
  }
}