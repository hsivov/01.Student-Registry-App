pipeline {
    agent any

    stages {
        stage('Install dependencies') {
            steps {
                bat 'npm install' 
            }
        }

        stage('Audit and fix') {
           steps {
                bat 'npm audit fix'
           }
        }

        stage('Run Integration Test') {
           steps {
                bat 'npm test'
           }
        }
    }
}
