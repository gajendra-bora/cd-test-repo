node {

    checkout scm

    env.DOCKER_API_VERSION="1.23"
    
    sh "git rev-parse --short HEAD > commit-id"

    tag = readFile('commit-id').replace("\n", "").replace("\r", "")
    appName = "hello-kenzan"

    stage "Deploy"

        kubernetesDeploy configs: "*.yaml", kubeconfigId: 'iot-dr-dev-1_auto_namespace'

}
