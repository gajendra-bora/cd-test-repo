node {
  checkout scm
  stage('Apply Kubernetes files') {
    sh label: '', script: '/usr/local/bin/kubectl --kubeconfig=/tmp/config apply -f helloworld-deployment.yaml'
    }
  }
}
