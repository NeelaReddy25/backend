pipeline {
    agent {
        label 'AGENT-1'
    }
    options {
        timeout (time:30, unit: 'MINUTES')
        disableConcurrentBuilds()
        ansiColor('xterm')
    }
    stages {
        stage ('read the version') {
            steps {
                script {
                    def packageJson = readJSON file: 'package.json'
                    def appVersion = packageJson.version
                    echo "applicatio version: $appversion"
                } 
            }
        }
    }
    post {
        always {
            echo 'I will always say Hello again!'
            echo "applicatio version: $appversion"
            deleteDir()
        }
        success {
            echo 'I will run when pipeline is success'
        }
        failure {
            echo 'I will run when pipeline is failure'
        }
    }
}