podTemplate(containers: [
        containerTemplate(
                name: 'nodejs',
                image: 'quay.io/openshift/origin-jenkins-agent-nodejs',
                ttyEnabled: true,
                command: 'cat',
                workingDir: '/home/jenkins/agent')
]) {

    node(POD_LABEL) {
        stage('Get a Nodejs project') {
            git url: 'https://github.com/jenbam/simple-node-js-react-npm-app.git'
            container('nodejs') {
                stage('Build a Nodejs project') {
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