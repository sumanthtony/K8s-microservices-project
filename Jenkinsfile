pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-id') {
                        sh 'docker build -t sumanthtony/checkoutservice:v1 .'
                    }
            }
        }
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-id') {
                        sh 'docker push sumanthtony/checkoutservice:v1'
                    }
                } 
            }
        }
    }
}
