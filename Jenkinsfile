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
                    env.dateStart = sh(script:'date "+%s"', returnStdout: true).trim()
                    echo "LS = ${env.LS}"
                    sh 'sleep 10'
                    // or if you access env variable in the shell command
                    sh 'echo $LS'
                    sh 'echo $dateStart'
                    sh 'echo $env.dateStart - $env.dateStop'
                    env.dateStop = sh(script:'date "+%s"', returnStdout: true).trim()
                    env.dateTime = sh(script:'let time=$env.dateStart-$env.dateStop && echo $time', returnStdout: true).trim()
                }
            }
        }
        stage("Sprawdzanie zmieniej"){
            steps{
                script{
                    sh 'echo $LS'
                }
                sh 'echo $env.dateStart - $env.dateStop'
                sh 'echo $env.dateTime'
            }
        }
    }
}
