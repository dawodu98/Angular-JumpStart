pipeline {
    agent any
    
    environment {
        PATH = "${tool name: 'Node.js', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
    }
    
    post {
        always {
            archiveArtifacts artifacts: 'dist/**', allowEmptyArchive: true
        }
    }
}