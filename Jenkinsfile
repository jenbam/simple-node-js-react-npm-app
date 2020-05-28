podTemplate(yaml:'''
spec:
  containers:
  - name: jnlp
    image: jenkins/jnlp-slave:4.0.1-1
    volumeMounts:
    - name: home-volume
      mountPath: /home/jenkins
    env:
    - name: HOME
      value: /home/jenkins
  - name: node
    image: node:6-alpine
    command: ['cat']
    tty: true
    volumeMounts:
    - name: home-volume
      mountPath: /home/jenkins
    env:
    - name: HOME
      value: /home/jenkins
    - name: MAVEN_OPTS
      value: -Duser.home=/home/jenkins
  volumes:
  - name: home-volume
    emptyDir: {}
''') {
  node('test-pod') {
    stage('Checkout') {
      checkout scm
    }
    stage('Build') {
      container('go-agent') {
        // This is where we build our code.
      }
    }
  }
}