pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t sumanthtony/service:v1 .'
            }
        }
        stage('Push to dockerHub') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-credentials') {
                        sh 'docker push sumanthtony/service:v1'
                    }
                }
            }
        }
    }
}
