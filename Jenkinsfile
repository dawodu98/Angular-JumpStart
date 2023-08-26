pipeline {
    agent any
    
    environment {
        // Define environment variables if needed
        NODE_HOME = tool name: 'node', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
        PATH = "${env.NODE_HOME}/bin:${env.PATH}"
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from your version control system (e.g., Git)
                checkout scm
            }
        }
        
        stage('Install Dependencies') {
            steps {
                // Install Node.js packages using npm
                sh "npm install"
            }
        }
        
        stage('Build') {
            steps {
                // Build your Angular project
                sh "npm run build"
            }
        }
        
        stage('Archive Artifacts') {
            steps {
                // Archive the built artifacts (dist folder in this case)
                archiveArtifacts artifacts: 'dist/**', allowEmptyArchive: true
            }
        }
    }
    
    post {
        always {
            // Clean up any temporary files or resources
            
            // For example, if you're using Docker, you might want to stop and remove containers
            // sh "docker stop my-angular-app-container"
            // sh "docker rm my-angular-app-container"
        }
        success {
            // Notify on success, send notifications, etc.
        }
        failure {
            // Notify on failure, send notifications, etc.
        }
    }
}