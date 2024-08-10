podTemplate(
  label: 'mypod',
  serviceAccount: 'jenkins',
  containers: [
    containerTemplate(
      name: 'docker',
      image: 'docker',
      command: 'cat',
      ttyEnabled: true,
      resourceRequestCpu: '100m',
      resourceLimitCpu: '300m',
      resourceRequestMemory: '300Mi',
      resourceLimitMemory: '500Mi'
    ),
    containerTemplate(
      name: 'kubectl',
      image: 'amaceog/kubectl',
      command: 'cat',
      ttyEnabled: true,
      resourceRequestCpu: '100m',
      resourceLimitCpu: '300m',
      resourceRequestMemory: '300Mi',
      resourceLimitMemory: '500Mi'
    ),
    containerTemplate(
      name: 'helm',
      image: 'alpine/helm:3.10.2',
      command: 'cat',
      ttyEnabled: true,
      resourceRequestCpu: '100m',
      resourceLimitCpu: '300m',
      resourceRequestMemory: '300Mi',
      resourceLimitMemory: '500Mi'
    )
  ],
  volumes: [
    hostPathVolume(mountPath: '/var/run/docker.sock', hostPath: '/var/run/docker.sock'),
    hostPathVolume(mountPath: '/usr/local/bin/helm', hostPath: '/usr/local/bin/helm')
  ]
) {
  node('mypod') {
    stage('Build Image') {
      container('docker') {
        sh 'docker build . -t icweiner'
      }
    }
  }
}

