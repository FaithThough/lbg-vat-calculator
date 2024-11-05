pipeline {
  agent any

  stages {
    stage('SonarQube Analysis') {
      environment {
        scannerHome = tool 'sonarqube'
      }
        steps {
            withSonarQubeEnv('sonar-qube-1') {        
              sh "${scannerHome}/bin/sonar-scanner"
            }   
        }
        timeout(time: 10, unit: 'MINUTES'){
            waitForQualityGate abortPipeline: true
        }
    }
  }
}