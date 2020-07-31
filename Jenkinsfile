pipeline {
  agent any

  triggers{
    bitbucketPush()
    pollSCM('* * * * *')
  }

  stages {
    stage('Pobieranie') {
      steps {
        script {
                    env.LS = sh(script:'ls -lah', returnStdout: true).trim()
                    echo "LS = ${env.LS}"
                    sh 'echo $LS'
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
