pipeline {
  environment {
    imagename = "shockerhub/myrepository"
    registryCredential = 'shockerhub_id'
    dockerImage = 'mydocshockimage'
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
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push("$BUILD_NUMBER")
             dockerImage.push('latest')
          }
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $imagename:$BUILD_NUMBER"
         sh "docker rmi $imagename:latest"
 
      }
    }
  }
}
