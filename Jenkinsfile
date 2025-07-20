pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-krushna', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://B2360D646A228AA391343C4ECB97DEED.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-krushna', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://B2360D646A228AA391343C4ECB97DEED.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
