pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }
        
        stage('Restore') {
            steps {
                script {
                    powershell 'dotnet restore'
                }
            }
        }
        
        stage('Build') {
            steps {
                script {
                    // Ensure build is done in Debug mode to match the test environment
                    powershell 'dotnet build --configuration Debug'
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    // Test command also configured for Debug mode
                    powershell 'dotnet test --configuration Debug'
                }
            }
        }
    }

    post {
        always {
            cleanWs() // Clean workspace after the build
        }
    }
}
