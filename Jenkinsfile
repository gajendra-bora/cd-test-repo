node {
  checkout scm
  stage('Apply Kubernetes files') {
    sh('/usr/local/bin/kubectl --kubeconfig=/tmp/config apply -f helloworld-deployment.yaml')
  }
}
