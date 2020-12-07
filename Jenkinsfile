node {
  stage('approval (test)') {
    input message: 'Approve for testing?',
      id: 'approval'
  }
  stage('build & deploy') {
    openshiftBuild bldCfg: 'hellopythonapp',
      namespace: 'dannt11',
      showBuildLogs: 'true'
    openshiftVerifyDeployment depCfg: 'hellopythonapp',
      namespace: 'dannt11'
  }
}
