pipeline {
    agent { docker 'maven:3-alpine' }
    triggers {
        pollSCM('')
    }
    stages {
        stage('Compile') {
            steps {
                echo 'Compiling....'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing....'
            }
        }
    }
}
