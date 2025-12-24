pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t sumanthtony/paymentservice:v1 .'
            }
        }
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred') {
                        sh 'docker push sumanthtony/paymentservice:v1'
                    }
                } 
            }
        }
    }
}
