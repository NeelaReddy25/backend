pipeline {
    agent {
        label 'AGENT-1'
    }
    options {
        timeout (time:30, unit: 'MINUTES')
        disableConcurrentBuilds()
        ansiColor('xterm')
    }
    environment {
        def appVersion = ' ' //variable declaration
    }
    stages {
        stage ('read the version') {
            steps {
                script {
                    def packageJson = readJSON file: 'package.json'
                    appVersion = packageJson.version
                    echo "applicatio version: $appversion"
                } 
            }
        }
        stage ('Install Dependencies') {
            steps {
                sh """
                npm install
                ls -ltr
                echo "applicatio version: $appversion"
                """
            }
        }
        stage ('Build') {
            steps {
                sh """
                zip -q -r backend-${appVersion} * -x Jenkinsfile -x backend-${appVersion}
                ls -ltr
                """
            }
        }
    }
    post {
        always {
            echo 'I will always say Hello again!'
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