pipeline {
    agent {
            label "master"
        }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh "/usr/bin/npm install"
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
    }
}
