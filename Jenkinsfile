podTemplate(
        containers: [
                containerTemplate(name: 'nodejs', image: 'quay.io/openshift/origin-jenkins-agent-nodejs', ttyEnabled: true, command: 'cat'),
                containerTemplate(name: 'docker', image:'trion/jenkins-docker-client')
        ],
        volumes: [
                hostPathVolume(mountPath: '/var/run/docker.sock', hostPath: '/var/run/docker.sock')
        ]
) {

    node(POD_LABEL) {
        stage('Get a Node project') {
            git 'https://github.com/jenbam/simple-node-js-react-npm-app.git'
            container('nodejs') {
                stage('Build a Nodejs project') {
                    sh 'curl -sL https://deb.nodesource.com/setup | sudo bash -'
                    sh 'sudo apt-get install -y nodejs'
                    sh 'npm install'
                }
                stage('Build Docker Image'){
                    container('docker'){
                        // This is where we build the Docker image
                    }
                }
            }
        }

    }
}
