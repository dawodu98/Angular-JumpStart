pipeline {
    agent any
    
    environment {
        NODE_HOME = tool name: 'node', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
        PATH = "${env.NODE_HOME}/bin:${env.PATH}"
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Install Dependencies') {
            steps {
                sh "npm install"
            }
        }
        
        stage('Build') {
            steps {
                sh "npm run build"
            }
        }
        
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'dist/**', allowEmptyArchive: true
            }
        }
    }
    
    post {
        always {
            // Clean up if needed
        }
        success {
            // Notify on success
        }
        failure {
            // Notify on failure
        }
    }
}
