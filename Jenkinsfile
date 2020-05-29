podTemplate(
        name: 'test-pod',
        label: 'test-pod',
        containers: [
                containerTemplate(name: 'nodejs', image: 'node:6-alpine', ttyEnabled: true, command: 'cat', args: '-p 3000:3000'),
                //containerTemplate(name: 'golang', image: 'golang:1.8.0', ttyEnabled: true, command: 'cat')
        ])
        {
            //node = the pod label
            node('test-pod') {
                //container = the container label
                stage('Build a Nodejs project') {
                    container('nodejs') {
                        sh 'echo hello world'
                        //sh 'npm install'
                    }
                }
/*            stage('Build Docker Image') {
              container('docker') {
                // This is where we build the Docker image
              }
            }*/
            }
        }


/*podTemplate(
        label: "skopeo-pod",
        cloud: "openshift",
        inheritFrom: "maven",
        containers: [
                containerTemplate(
                        name: "jnlp",
                        image: "docker-registry.default.svc:5000/${GUID}-jenkins/jenkins-agent-maven-skopeo:latest",
                        resourceRequestMemory: "1Gi",
                        resourceLimitMemory: "2Gi"
                )
        ]
) {
    node('skopeo-pod') {

    }
}*/

/*
podTemplate(containers: [
    containerTemplate(name: 'maven', image: 'maven:3.3.9-jdk-8-alpine', ttyEnabled: true, command: 'cat'),
    containerTemplate(name: 'golang', image: 'golang:1.8.0', ttyEnabled: true, command: 'cat')
  ]) {

    node(POD_LABEL) {
        stage('Get a Maven project') {
            git 'https://github.com/jenkinsci/kubernetes-plugin.git'
            container('maven') {
                stage('Build a Maven project') {
                    sh 'mvn -B clean install'
                }
            }
        }

        stage('Get a Golang project') {
            git url: 'https://github.com/hashicorp/terraform.git'
            container('golang') {
                stage('Build a Go project') {
                    sh """
                    mkdir -p /go/src/github.com/hashicorp
                    ln -s `pwd` /go/src/github.com/hashicorp/terraform
                    cd /go/src/github.com/hashicorp/terraform && make core-dev
                    """
                }
            }
        }

    }
}
 */


/*podTemplate(yaml:'''
spec:
  containers:
  - name: jnlp
    image: jenkins/jnlp-slave
    volumeMounts:
    - name: home-volume
      mountPath: /home/jenkins
    env:
    - name: HOME
      value: /home/jenkins
  - name: nodejs
    image: node:6-alpine
    command: ['cat']
    tty: true
    volumeMounts:
    - name: home-volume
      mountPath: /home/jenkins
    env:
    - name: HOME
      value: /home/jenkins
  volumes:
  - name: home-volume
    emptyDir: {}
''') {
    node(POD_LABEL) {
        stage('Build a Nodejs project') {
            container('nodejs') {
                sh 'npm install'
            }
        }
    }
}*/
