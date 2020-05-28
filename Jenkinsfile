podTemplate(yaml:'''
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
}
