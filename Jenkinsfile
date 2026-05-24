pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
             steps {
                sh 'echo "Executando Docker Build..."'
            }
            steps {
                sh 'echo "Building..."'
            }
        }
        stage('Push Docker Image') {
            steps {
                sh 'echo "Executando Push do Docker Image..."'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Executando o comando kubeclt apply"'
            }
        }
    }
}