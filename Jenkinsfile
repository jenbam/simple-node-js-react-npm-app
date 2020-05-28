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
  - name: dind
    image: docker:19.03
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
  node(POD_LABEL) {
    stage('Build a Maven project') {
      container('maven') {
        git 'https://github.com/jenkinsci/kubernetes-plugin.git'
        sh 'mvn -B clean package -DskipTests'
      }
    }
  }
}
