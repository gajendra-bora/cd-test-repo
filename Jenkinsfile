pipeline {
    agent any

    parameters {
       string defaultValue: 'devhub-docker.cisco.com/iot-dockersandbox/gbora/rest-hello-world-fanuc:3', description: '', name: 'IMAGE_NAME', trim: false
    }
    options {
        buildDiscarder(logRotator(numToKeepStr: '30', artifactNumToKeepStr: '30'))
        disableConcurrentBuilds()
    }

    stages {
        stage ('Update workspace with latest image') {
            steps {
                checkout scm
                sh 'sed -i s/image:.*/image:${IMAGE_NAME}/g helloworld-deployment.yaml'
            }
        }

        stage ('Deploy image to EKS automation cluster') {
            steps {
                sh '/usr/local/bin/kubectl --kubeconfig=/tmp/config apply -f helloworld-deployment.yaml'
            }
        }
    }
}
