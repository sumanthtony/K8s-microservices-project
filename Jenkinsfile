pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-id') {
                        sh 'docker build -t sumanthtony/cartservice:v1 .'
                    }
            }
        }
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-id') {
                        sh 'docker push sumanthtony/cartservice:v1'
                    }
                } 
            }
        }
    }
}
