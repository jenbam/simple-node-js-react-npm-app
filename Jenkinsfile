pipeline {
    agent {
        kubernetes {
            label podlabel
            yaml """
    kind: Pod
    metadata:
      name: jenkins-slave
    spec:
      containers:
      - name: kaniko
        image: gcr.io/kaniko-project/executor:debug
        imagePullPolicy: Always
        command:
        - /busybox/cat
        tty: true
        volumeMounts:
          - name: aws-secret
            mountPath: /root/.aws/
          - name: docker-registry-config
            mountPath: /kaniko/.docker
      restartPolicy: Never
      volumes:
        - name: aws-secret
          secret:
            secretName: aws-secret
        - name: docker-registry-config
          configMap:
            name: docker-registry-config
    """
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
