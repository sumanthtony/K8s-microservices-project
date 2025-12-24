pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t sumanthtony/currencyservice:v1 .'
            }
        }
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred') {
                        sh 'docker push sumanthtony/currencyservice:v1'
                    }
                } 
            }
        }
    }
}
