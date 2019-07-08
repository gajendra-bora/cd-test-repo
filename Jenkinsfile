node {

    checkout scm

    stage "Deploy"

        withKubeConfig([credentialsId: 'iot-dr-dev-1_auto_namespace', serverUrl: 'https://FC24440CA59CB0FF072D5FBE111D9DCB.sk1.us-east-1.eks.amazonaws.com']) {
            /usr/local/bin/kubectl apply -f helloworld-deployment.yaml
        }

}
