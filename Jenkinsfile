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
        script {
                    env.LS = sh(script:'ls -lah', returnStdout: true).trim()
                    echo "LS = ${env.LS}"
                    // or if you access env variable in the shell command
                    sh 'echo $LS'
                }
    }

    stage('Generowanie raportu') {
      steps {
        junit(allowEmptyResults: true, testResults: 'report/*.xml')
      }
    }

  }
}
