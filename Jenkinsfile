node{
    stage("Clone") {
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/dinara21/shared-tools.git']]])
}
    stage("Build"){
        sh "docker build -t tools ."
    }

    stage("Tagging"){
        sh "docker tag tools:latest ${AWS_ACCOUNT}.dkr.ecr.us-east-2.amazonaws.com/tools:latest"
    }

    stage("Autheticate"){
        sh "aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin ${AWS_ACCOUNT}.dkr.ecr.us-east-2.amazonaws.com"

    }
    stage("Push Image"){
        sh "docker push ${AWS_ACCOUNT}.dkr.ecr.us-east-2.amazonaws.com/tools:latest"
    }

}