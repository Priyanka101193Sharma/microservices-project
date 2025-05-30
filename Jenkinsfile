pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-priyanka1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://F038A3C111B102E6160D52E2F780FCF3.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-priyanka1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://F038A3C111B102E6160D52E2F780FCF3.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
