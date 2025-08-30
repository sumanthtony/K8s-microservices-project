pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks-1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://89214529042F345969A03B7B5C112BAF.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks-1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://89214529042F345969A03B7B5C112BAF.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
