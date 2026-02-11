pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eksclus1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://88C7D37C0480EF02A07BC701A33F38E9.yl4.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eksclus1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://88C7D37C0480EF02A07BC701A33F38E9.yl4.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
