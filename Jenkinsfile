podTemplate(containers: [
    containerTemplate(name: 'golang', image: 'vincmarz/go-http-server')
  ]) {

    node(POD_LABEL) {
        stage('Get a Golang project') {
            git url: 'https://github.com/vincmarz/ci-cd-example.git'
            container('golang') {
                stage('Build a Go project') {
                    sh """
                    cd /go/src
                    """
                }
            }
        }

    }
}
