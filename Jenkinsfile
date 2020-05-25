pipeline {
    agent {
            label "master"
        }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
          agent {
             node {
               label "jenkins-slave-npm"
                }
            }
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
    }
}
