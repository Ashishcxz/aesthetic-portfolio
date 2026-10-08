pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'git@github.com:Ashishcxz/aesthetic-portfolio.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ashish5554545/aesthetic-portfolio:latest .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push ashish5554545/aesthetic-portfolio:latest'
            }
        }
    }
}
