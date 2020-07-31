pipeline {
    agent any
     
    triggers{
    pollSCM('* * * * *')
  }

    stages {
        stage("Env Variables") {
            steps {
                script {
                    env.LS = sh(script:'ls -lah', returnStdout: true).trim()
                    env.date = sh(script:'date "+%s"', returnStdout: true).trim()
                    echo "LS = ${env.LS}"
                    // or if you access env variable in the shell command
                    sh 'echo $LS'
                    sh 'echo $date'
                }
            }
        }
        stage("Sprawdzanie zmieniej"){
            steps{
                script{
                    sh 'echo $LS'
                }
                sh 'echo $date'
            }
        }
    }
}
