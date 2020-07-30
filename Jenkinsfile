pipeline {
  agent any
  triggers{
    bitbucketPush()
    pollSCM('* * * * *')
  }
  stages {
    stage('Pobieranie') {
      agent any
      steps {
        git(changelog: true, poll: true, url: 'https://gitlab.com/en696/bash.git', branch: 'master')
        timestamps() {
          sh '''
              echo test
              hostname
              '''
        }

      }
    }

    stage('Generowanie raportu') {
      steps {
        junit(allowEmptyResults: true, testResults: 'report/*.xml')
      }
    }

  }
}
