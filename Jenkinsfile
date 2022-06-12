node{
    stage("Clone") {
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/dinara21/shared-tools.git']]])
}
    stage("Build"){
        sh "docker build -t tools ."
    }

    stage("Tagging"){
        sh "properties([parameters([string(defaultValue: '736098766695', description: 'Please provide your account', name: 'AWS_ACCOUNT', trim: true)])])"
    }

    Stage("Autheticate"){
        sh "aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 736098766695.dkr.ecr.us-east-2.amazonaws.com"

    }
    stage("Push Image"){
        sh "docker push 736098766695.dkr.ecr.us-east-2.amazonaws.com/tools:latest"
    }

}