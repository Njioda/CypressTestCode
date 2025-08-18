pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building...'
        // Add your build steps here
      }
    }
    stage('Test') {
      steps {
        echo 'Running Cypress tests...'
        bat 'cypress run --reporter mochawesome --reporter-options reportDir=cypress/reports,reportFilename=report'
        // Or, if you're using a specific command:
        // sh 'npm run cypress:run'
      }
    }
  }
  post {
    always {
      archiveArtifacts artifacts: 'cypress/reports/*', fingerprint: true
      publishHTML([
        target: [
          reportName: 'Cypress Report',
          reportDir: 'cypress/reports',
          reportFiles: 'report.html',
          reportTitle: 'Cypress Test Report'
        ]
      ])
    }
  }
}
