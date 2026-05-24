pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
             steps {
                sh 'echo "Executando Docker Build..."'
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
