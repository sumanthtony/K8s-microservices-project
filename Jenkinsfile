pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'my-cluster', contextName: '', credentialsId: 'k8s-secret', namespace: 'webapps', serverUrl: 'https://0CA43D235B5426E5ADE6B9FBC90C145A.sk1.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'my-cluster', contextName: '', credentialsId: 'k8s-secret', namespace: 'webapps', serverUrl: 'https://0CA43D235B5426E5ADE6B9FBC90C145A.sk1.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
