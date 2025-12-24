pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t sumanthtony/loadgeneratorservice:v1 .'
            }
        }
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred') {
                        sh 'docker push sumanthtony/loadgeneratorservice:v1'
                    }
                } 
            }
        }
    }
}
