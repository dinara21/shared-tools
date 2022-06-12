node{
    stage("Clone") {
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/dinara21/shared-tools.git']]])
}
    stage("Build"){
        sh "docker build -t tools ."
    }

}