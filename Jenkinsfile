node {

    checkout scm

    env.DOCKER_API_VERSION="1.23"
    
    sh "git rev-parse --short HEAD > commit-id"

    tag = readFile('commit-id').replace("\n", "").replace("\r", "")
    appName = "hello-kenzan"

    stage "Deploy"

        withKubeConfig([credentialsId: 'iot-dr-dev-1_auto_namespace']) {
            sh '/usr/local/bin/kubectl apply -f helloworld-deployment.yaml'
        }

}
