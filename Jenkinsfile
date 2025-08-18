pipeline {
    agent any

    stages {
        stage('Install') {
            steps {
                bat 'npm ci'
            }
        }

        stage('Run Cypress Tests') {
            steps {
                bat 'npx cypress run'
            }
        }

        stage('Generate Report') {
            steps {
                bat 'npm run posttest'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'cypress/reports/**/*.*', allowEmptyArchive: true
            }
        }
    }

    post {
        always {
            //junit 'cypress/reports/**/*.xml' // if using JUnit XML
        }
    }
}
