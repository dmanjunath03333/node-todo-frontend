
pipeline {
  environment {
    registry ="dmanjunath03333/node=todo-install"
    registryCrednetials='dockerhub'
    dockerImage=''
    containerId=sh(script: 'docker ps -aqf "name=node-app",returnStdout:true)

}
                   
  agent any
  stages {
  stage ('Cloning Git') {
    steps {
      git 'https://github.com/dmanjunath03333/node-todo-frontend'
    }
  }
stage ('Build') {
  steps {
   sh 'npm install' 
  }
}
  
stage('Test') {
  steps{
   sh 'npm test' 
  }
}
  
  stage('Building Image') {
    steps{
      script {
        dockerImage= docker.build registry+ ":BUILD_NUMBER"
      }
  }
}
