pipeline {
  agent any
  stages {
    stage('Pierwszy krok') {
      agent any
      steps {
        git(changelog: true, poll: true, url: 'https://gitlab.com/en696/bash.git', branch: 'master')
      }
    }

  }
}