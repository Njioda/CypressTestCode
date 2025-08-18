pipeline {
    agent any
    tools {
    nodejs "24.3.0"  // matches the name configured in Jenkin
  }

    environment {
        CYPRESS_CACHE_FOLDER = "${WORKSPACE}/.cache/Cypress"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/your-org/your-repo.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm ci'
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

        stage('Publish Test Results') {
            steps {
                junit 'cypress/reports/**/*.xml' // if you generate JUnit reports
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
    }
}
