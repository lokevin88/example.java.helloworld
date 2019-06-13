pipeline {
    agent { docker 'maven' }
    triggers {
        pollSCM('')
    }
    stages {
        stage('Compile') {
            steps {
                echo 'Compiling....'
            }
        }
        stage('Example Build') {
            agent { docker 'maven:3-alpine' } 
            steps {
                echo 'Hello, Maven'
                sh 'mvn --version'
            }
        }
        stage('Sonarqube 1') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.4.1.1168:sonar'
                }
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
