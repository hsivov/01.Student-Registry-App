pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'npm install' 
            }
        }

        stage('Test') {
           steps {
                sh 'npm test'
           }
        }

        stage('Deploy to Docker Hub') {
           environment {
                DOCKERHUB_CREDS = credentials('13ab3260-4a21-4bb2-8406-5b787b519359')
           }
           steps {
                sh 'sudo docker build -t hsivov/students-app .'
                sh 'sudo docker login -u $DOCKERHUB_CREDS_USR -p $DOCKERHUB_CREDS_PSW'
                sh 'sudo docker push hsivov/students-app'
           }
        }

        stage('Deploy to production') {
            steps {
                sh 'sudo docker pull hsivov/students-app'
                sh 'sudo docker compose -f docker-compose.yml up -d'
            }
        }
    }
}