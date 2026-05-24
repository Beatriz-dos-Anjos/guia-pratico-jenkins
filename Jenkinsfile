pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    def dockerapp = docker.build("beatrizanjos/guia-jenkins:${env.BUILD_ID}", '-f ./src/Dockerfile ./src')
                    env.DOCKER_IMAGE = dockerapp.imageName()
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    def dockerapp = docker.image("beatrizanjos/guia-jenkins:${env.BUILD_ID}")
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub') {
                        dockerapp.push('latest')
                        dockerapp.push("${env.BUILD_ID}")
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                withKubeConfig([credentialsId: 'kubeconfig']) {
                    sh 'kubectl apply -f src/k8s/deployment.yaml'
                }
            }
        }
    }
}
