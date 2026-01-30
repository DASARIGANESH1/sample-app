pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/DASARIGANESH1/sample-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t sample-app:latest .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop sample-app || true
                docker rm sample-app || true
                docker run -d -p 3000:3000 --name sample-app sample-app:latest
                '''
            }
        }
    }
}
