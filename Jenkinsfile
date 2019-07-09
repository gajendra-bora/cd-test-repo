pipeline {
    agent any

    options {
        buildDiscarder(logRotator(numToKeepStr: '30', artifactNumToKeepStr: '30'))
        disableConcurrentBuilds()
    }

    stages {
        stage ('Update workspace with latest image') {
            steps {
                script {
                    sed -i 's/image\:.*/image:$IMAGE_NAME/g' helloworld-deployment.yaml
                }
            }
        }
    }

    stages {
        stage ('Deploy image to EKS automation cluster') {
            steps {
                script {
                     /usr/local/bin/kubectl --kubeconfig=/tmp/config apply -f helloworld-deployment.yaml
                }
            }
        }
    }
}
}
