node {
 stage('SCM') {
 checkout scm
 }
 stage ('Build and Push Image to Docker Registry') {
 dir("jenkins"){
 sh("echo $USER")
 def newApp = docker.build "pacman:${env.BUILD_TAG}"
 def newAppLatest = docker.build "pacman:latest"
 }
 }
}
