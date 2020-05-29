podTemplate(containers: [
        containerTemplate(name: 'maven', image: 'maven:3.3.9-jdk-8-alpine', ttyEnabled: true, command: 'cat'),
        containerTemplate(name: 'nodejs', image: 'quay.io/openshift/origin-jenkins-agent-nodejs', ttyEnabled: true, command: 'cat')
]) {

    node(POD_LABEL) {
        stage('Get a Nodejs project') {
            git url: 'https://github.com/jenbam/simple-node-js-react-npm-app.git'
            container('golang') {
                stage('Build a Go project') {
                    sh """
                    curl -sL https://deb.nodesource.com/setup | sudo bash -
                    sudo apt-get install -y nodejs
                    npm install
                    """
                }
            }
        }

    }
}