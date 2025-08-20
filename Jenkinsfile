pipeline {
    agent any
    tools {
    nodejs "24.3.0"  // matches the name configured in Jenkin
  } 

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/Njioda/CypressTestCode.git'
            }
        }
        

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

        stage('Archive Test Artifacts') {
            steps {
                archiveArtifacts artifacts: 'cypress/videos/**, cypress/screenshots/**', allowEmptyArchive: true
            }
        }
   
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
    }
}
