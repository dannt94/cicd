node {
  stage('build & deploy') {
    openshiftBuild bldCfg: 'hellopythonapp',
      namespace: 'dannt11-development',
      showBuildLogs: 'true'
    openshiftVerifyDeployment depCfg: 'hellopythonapp',
      namespace: 'dannt11-development'
  }
  stage('approval (test)') {
    input message: 'Approve for testing?',
      id: 'approval'
  }
  stage('deploy to test') {
    openshiftTag srcStream: 'hellopythonapp',
      namespace: 'dannt11-development',
      srcTag: 'latest',
      destinationNamespace: 'dannt11-testing',
      destStream: 'hellopythonapp',
      destTag: 'test'
    openshiftVerifyDeployment depCfg: 'hellopythonapp',
      namespace: 'dannt11-testing'
  }
  stage('approval (production)') {
    input message: 'Approve for production?',
      id: 'approval'
  }
  stage('deploy to production') {
    openshiftTag srcStream: 'hellopythonapp',
      namespace: 'dannt11-development',
      srcTag: 'latest',
      destinationNamespace: 'dannt11-production',
      destStream: 'hellopythonapp',
      destTag: 'prod'
    openshiftVerifyDeployment depCfg: 'hellopythonapp',
      namespace: 'dannt11-production'
  }
}
