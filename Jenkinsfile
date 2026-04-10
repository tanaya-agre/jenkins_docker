pipeline {
agent any

environment {
Docker_image= 'hello-world-python:latest' 
}

stages {
stage('Checkout') {
steps {
git branch: 'main', url:
'https://github.com/tanaya-agre/jenkins_docker.git'
}
}
stage('Docker build') {
steps {
script {
if (fileExists('Dockerfile')) {
sh "docker build -t ${env.Docker_image} ."
} else {
error "Dockerfile not found in the workspace. please create one for your python appication"
}
}
}
}
stage('Docker Run (Optional)') {
steps {
sh "docker run --rm ${env.Docker_image}"
}
}
}
post {
success {
echo 'success'
}
failure {
echo 'failure'
}
}
}
