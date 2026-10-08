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
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub',
                    usernameVariable: 'DOCKER_USERNAME',
                    passwordVariable: 'DOCKER_PASSWORD'
                )]) {
                    sh '''
                        echo "$DOCKER_PASSWORD" | docker login -u "$DOCKER_USERNAME" --password-stdin
                        docker push ashish5554545/aesthetic-portfolio:latest
                        docker logout
                    '''
                }
            }
        }
    }
}
