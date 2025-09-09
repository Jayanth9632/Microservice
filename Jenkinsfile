pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                script {
                    withKubeCredentials([[
                        credentialsId: 'k8-token',
                        serverUrl: 'https://9D07D7A48F9C9055FE49958A1B9BCE94.gr7.us-east-1.eks.amazonaws.com',
                        clusterName: 'EKS-1',
                        namespace: 'webapps',
                        caCertificate: ''
                    ]]) {
                        sh 'kubectl apply -f deployment-service.yml'
                    }
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                script {
                    withKubeCredentials([[
                        credentialsId: 'k8-token',
                        serverUrl: 'https://9D07D7A48F9C9055FE49958A1B9BCE94.gr7.us-east-1.eks.amazonaws.com',
                        clusterName: 'EKS-1',
                        namespace: 'webapps',
                        caCertificate: ''
                    ]]) {
                        sh 'kubectl get svc -n webapps'
                    }
                }
            }
        }
    }
}
