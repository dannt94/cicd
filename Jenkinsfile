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
      destTag: 'prod'
    openshiftVerifyDeployment depCfg: 'hellopythonapp',
      namespace: 'dannt11'
  }
}
