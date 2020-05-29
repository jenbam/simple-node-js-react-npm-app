podTemplate(
        containers: [
                containerTemplate(name: 'nodejs', image: 'quay.io/openshift/origin-jenkins-agent-nodejs', ttyEnabled: true, command: 'cat')
        ]
) {

    node(POD_LABEL) {
        stage('Get a Node project') {
            git 'https://github.com/jenbam/simple-node-js-react-npm-app.git'
            container('nodejs') {
                stage('Build a Nodejs project') {
                    sh(script: 'npm install', returnStdout: true)

                }
            }
        }

    }
}
