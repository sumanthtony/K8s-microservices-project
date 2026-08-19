pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-id') {
                        sh 'docker build -t sumanthtony/shippingservice:v2 .'
                    }
            }
        }
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-id') {
                        sh 'docker push sumanthtony/shippingservice:v2'
                    }
                } 
            }
        }
    }
}
}
