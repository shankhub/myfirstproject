pipeline {
  environment {
    imagename = "shockerhub/myrepository"
    registryCredential = 'shockerhub_id'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git([url: 'https://github.com/shankhub/myfirstproject.git', branch: 'master', credentialsId: 'shankhub_id'])
      }
    }
    stage('Building image') {
      steps{
        script {
         sh 'docker build -t shockerhub/mytestimage:latest .' 
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
         dockerImage = docker.build registry 
          }
        }
      }
    }
  }
