node {

    checkout scm

    env.DOCKER_API_VERSION="1.23"
    
    sh "git rev-parse --short HEAD > commit-id"

    tag = readFile('commit-id').replace("\n", "").replace("\r", "")
    appName = "hello-kenzan"

    stage "Deploy"

        withKubeConfig([credentialsId: 'iot-dr-dev-1_auto_namespace', serverUrl: 'https://FC24440CA59CB0FF072D5FBE111D9DCB.sk1.us-east-1.eks.amazonaws.com']) {
            sh 'kubectl apply -f helloworld-deployment.yaml'
        }

}
