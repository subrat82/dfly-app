pipeline {
  environment {
    registry = "subratit/projects-16th-dec"
    registryCredential = '076eed1a-ddda-4fcc-b8bd-5fbf6fa738fd'
    //registryCredential = 'dockeradmin'
    dockerImage = ''
  }
  agent any
  stages {
    stage(‘Build’) {
       steps {
         sh 'echo  "Sample build passed"'
       }
    }
    stage(‘Test’) {
      steps {
        sh 'echo  "Sample test passed"'
      }
    }
    stage(‘Building’) {
      steps{
        script {
          dockerImage = docker.build registry
          sh 'echo  "Sample build passed"'
        }
      }
    }
    stage(‘Deploy’) {
      steps{
         script {
            docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
            sh 'echo  "Sample deploy passed"'
          }
        }
      }
    }
  }
}
