pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building...'
        // Add your build steps here
      }
    }

  tools {
    nodejs "24.3.0"  // matches the name configured in Jenkin
  }

 stages {
      stage('Install Dependencies') {
          steps {
              bat 'npm ci'
          }
      }
      stage('Run Cypress Tests') {
          steps {
              bat 'npx cypress run'
          }
      }
  
  }
  post {
        always {
             archiveArtifacts artifacts: 'cypress/videos/*'
             archiveArtifacts artifacts: 'cypress/reports/**'
        }
    }
}
}

