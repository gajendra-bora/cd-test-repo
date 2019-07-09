pipeline {
    agent any

    parameters {
       string defaultValue: '', description: '', name: 'IMAGE_NAME', trim: false
    }
    options {
        buildDiscarder(logRotator(numToKeepStr: '30', artifactNumToKeepStr: '30'))
        disableConcurrentBuilds()
    }

    stages {
        stage ('Update workspace with latest image') {
            steps {
                checkout scm
                sh 'sed -i 's/image:.*/image:myimage/g' helloworld-deployment.yaml'
            }
        }

        stage ('Deploy image to EKS automation cluster') {
            steps {
                sh '/usr/local/bin/kubectl --kubeconfig=/tmp/config apply -f helloworld-deployment.yaml'
            }
        }
    }
}
