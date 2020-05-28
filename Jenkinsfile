pipeline {
    agent {
        kubernetes {
          label 'jenkins-slave'
          defaultContainer 'jnlp'
          yaml """
    apiVersion: v1
    kind: Pod
    spec:
      containers:
      - name: dind
        image: docker:18.09-dind
        securityContext:
          privileged: true
      - name: docker
        env:
        - name: DOCKER_HOST
          value: 127.0.0.1
        image: docker:18.09
        command:
        - cat
        tty: true
      - name: nodejs
        image: openshift/jenkins-agent-nodejs-8-centos7
        command:
        - cat
        tty: true
    """
        }
      }

    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}