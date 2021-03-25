pipeline {
    agent any
    tools {
        go 'go1.14'
        'org.jenkinsci.plugins.docker.commons.tools.DockerTool' 'default-docker'
    }
    environment {
        GO111MODULE = 'on'
        CGO_ENABLED = 0
        registry = "vincmarz/go-http-server"
        GOCACHE = "/tmp"
    }
    stages {
         stage('Pre Test') {
            steps {
                echo 'Installing dependencies'
                sh 'go version'
                sh 'mkdir -p /home/jenkins/go/src/hello-world'
                sh 'cd /home/jenkins/go/src'
                sh 'cp -r ${WORKSPACE}/* /home/jenkins/go/src/hello-world'
                //Create go.mod file
                sh 'go mod init hello-world/main'
                // Build the app
                sh 'go build'
            }
         }
        stage('Test') {
            steps {
                sh 'mkdir -p /home/jenkins/go/src/hello-world'
                sh 'cd /home/jenkins/go/src'
                sh 'cp -r ${WORKSPACE}/* /home/jenkins/go/src/hello-world'
                echo 'Remove cached test results'
                sh 'go clean -cache'
                echo 'Run Unit Tests'
                sh 'go test ./... -v -short'
            }
        }
        stage('Publish') {
            environment {
                registryCredential = 'DockerHub'
            }
            steps {
                sh 'docker version'
                script {
                    def appimage = docker.build registry + ":$BUILD_NUMBER"
                    docker.withRegistry( '', registryCredential ) {
                        appimage.push()
                        appimage.push('latest')
                     }
                    }
            }
        }         
    }
}
