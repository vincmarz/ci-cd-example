podTemplate(containers: [
    containerTemplate(name: 'golang', image: 'vincmarz/go-http-server', ttyEnabled: true)
  ]) {

    node(POD_LABEL) {
        stage('Get a Golang project') {
            git url: 'https://github.com/vincmarz/ci-cd-example.git'
            container('golang') {
                stage('Build a Go project') {
                    sh """
                    cd ${GOPATH}/src
                    mkdir -p ${GOPATH}/src/hello-world
                    cp -r ${WORKSPACE}/* ${GOPATH}/src/hello-world
                    go build
                    """
                }
            }
        }

    }
}
