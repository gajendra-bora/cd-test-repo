node {
  checkout scm
  stage('Apply Kubernetes files') {
    withEnv(['PATH+EXTRA=/usr/local/bin']) {
      sh('/usr/local/bin/kubectl --kubeconfig=/tmp/config apply -f helloworld-deployment.yaml')
    }
  }
}
