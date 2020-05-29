podTemplate(
        name: 'test-pod',
        label: 'test-pod',
        containers: [
                containerTemplate(name: 'jnlp', image: 'jenkins/jnlp-slave'),
                containerTemplate(name: 'nodejs', image: 'node:6-alpine'),
        ],
        volumes: [
                emptyDirVolume(mountPath: '/home/jenkins', memory: true),
                hostPathVolume(mountPath: '/home/jenkins', hostPath: '/home/jenkins')
        ])
        {
          //node = the pod label
          node('test-pod') {
            //container = the container label
            stage('Build a Nodejs project') {
              container('nodejs') {
                  sh 'npm install'
              }
            }
            stage('Build Docker Image') {
              container('docker') {
                // This is where we build the Docker image
              }
            }
          }
        }


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
