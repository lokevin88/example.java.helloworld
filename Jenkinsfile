pipeline {
    agent any
    triggers {
        pollSCM('')
    }
    stages {
        stage('Compile') {
            steps {
                echo 'Compiling....'
            }
        }
        stage('Sonarqube 2') {
            environment {
                scannerHome = tool 'SonarQubeScanner'
            }
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
                timeout(time: 10, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing....'
            }
        }
    }
}
