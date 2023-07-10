node {
 stage('SCM') {
 checkout scm
 }
 stage('test user') {
 sh "echo $USER"
 }
 stage ('Build and Push Image to Docker Registry') {
 dir("jenkins"){
 def newApp = docker.build "pacman:${env.BUILD_TAG}"
 def newAppLatest = docker.build "pacman:latest"
 }
 }
}
