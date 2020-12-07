node {
  stage('approval (production)') {
    input message: 'Approve for production?',
      id: 'approval'
  }
  stage('deploy to production') {
    openshiftTag srcStream: 'hellopythonapp',
      namespace: 'dannt11',
      srcTag: 'latest',
      destinationNamespace: 'dannt11',
      destStream: 'hellopythonapp',
      destTag: 'latest'
    openshiftVerifyDeployment depCfg: 'hellopythonapp',
      namespace: 'dannt11'
  }
}
