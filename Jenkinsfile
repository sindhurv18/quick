pipeline {
    agent any
    environment {
        // Define environment variables to store Kubernetes configuration
        KUBECONFIG = '/tmp/kubeconfig'
    }
    stages { 
        stage('Checkout') {
            steps {
                script {
                    // Clone the repository containing Kubernetes manifest files
                    git url: 'https://github.com/sindhurv18/quick.git', branch: 'master'
                }
            }
        }

       stage('Check Kubernetes Cluster') {
            steps {
                // Use the withCredentials block to securely access the kubeconfig file
                withCredentials([file(credentialsId: 'rancher', variable: 'kubeconfig')]) {
                    
                    // Get the name of the Kubernetes cluster
                    sh 'kubectl delete secret registry-credentials -n devl-gpmportal'
            }
        }
    }
}

