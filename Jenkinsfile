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

        
        stage('bulding') {
            steps{
                echo 'Building the appication.'             
            }
        }

        stage('Run Cypress Tests') {
            steps {
                bat 'npx cypress run'
            }
        }

        stage('Archive Test Artifacts') {
            steps {
                //archiveArtifacts artifacts: 'cypress/videos/**, cypress/screenshots/**', allowEmptyArchive: true
                archiveArtifacts artifacts: 'cypress/reports/**'
            }
        }
   
    }

    post {
        always {
            //publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, icon: '', keepAll: true, reportDir: 'cypress/reports/html/', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
        }
    }
}
