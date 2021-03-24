pipeline {
    agent any
    tools {
        go 'go1.14'
    }
    environment {
        GO111MODULE = 'on'
        CGO_ENABLED = 0 
        GOPATH = "${JENKINS_HOME}/jobs/${JOB_NAME}/builds/${BUILD_ID}"
        registry = "vincmarz/go-http-server"
        GOCACHE = "/tmp"
    }
    stages {
         stage('Pre Test') {
            steps {
                echo 'Installing dependencies'
                sh 'go version'
                sh 'go get -u golang.org/x/lint/golint'
                sh 'cd ${GOPATH}/src'
                sh 'mkdir -p ${GOPATH}/src/hello-world'
            }
        }         
    }
          
}
