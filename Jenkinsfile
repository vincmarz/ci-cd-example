pipeline {
 environment {
    registry = "vincmarz/ci-cd-example"
    registryCredential = 'DockerHub'
  }
 agent any
   stages {
    stage('build') {
      steps {
         sh 'echo "Hello, World (Docker for Developers)"'
      }
    }
   }
}  
