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
                    sh 'kubectl config get-clusters'
                    
                    // List pods in the gpmportal namespace
                    sh 'kubectl get pods'
                    
                    // List pods in the devl-gpmportal namespace
                    sh 'kubectl get pods'
                    sh 'kubectl apply -f secret.yaml'

                    sh 'kubectl get secrets'
                }
            }
        }
    }
}
