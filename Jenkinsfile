pipeline {
 agent any
 environment {
    registry = "vincmarz/ci-cd-example"
    registryCredential = 'DockerHub'
  }
  stages {
    stage('Hello') {
      steps {
         sh 'echo "Hello, World (Docker for Developers)"'
      }
    }
    stage('Build') { 
      agent {
          docker { 
            image 'golang' 
           }
      }
      steps {
         sh 'echo "Hello build"'
      }  
    }
  } 
}  
