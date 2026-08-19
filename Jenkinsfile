pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-id') {
                        sh 'docker build -t sumanthtony/productcatalogservice:v2 .'
                    }
                }
            }
        }
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-id') {
                        sh 'docker push sumanthtony/productcatalogservice:v2'
                    }
                }
            }
        }
    }
}
