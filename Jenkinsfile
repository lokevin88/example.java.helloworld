pipeline {
    agent any
    triggers {
        pollSCM('* * * * *')
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
