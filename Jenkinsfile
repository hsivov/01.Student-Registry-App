pipeline {
    agent any

    stages {
        stage('Install dependencies') {
            steps {
                bat 'npm install' 
            }
        }

        stage('Audit') {
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
