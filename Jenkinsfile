node {
 stage('SCM') {
 checkout scm
 }
 stage('Pacman Checkout') {
  git 'https://github.com/ilkilab/pacman.git'
 }
 stage ('Build and Push Image to Docker Registry') {
 dir("pacman/docker"){
 def newApp = docker.build "pacman:${env.BUILD_TAG}"
 def newAppLatest = docker.build "pacman:latest"
 }
 }
}
