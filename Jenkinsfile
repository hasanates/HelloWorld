pipeline {
    agent any
    stages {
        stage('Restore') {
            steps {
                script {
                    // Restore .NET dependencies for the solution using PowerShell
                    powershell 'dotnet restore HelloWorld.sln'
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    // Build the solution in Release configuration using PowerShell
                    powershell 'dotnet build HelloWorld.sln --configuration Release'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Run tests for the solution using PowerShell
                    powershell 'dotnet test HelloWorld.sln --no-build'
                }
            }
        }
    }
    post {
        always {
            // Clean up the workspace after the build
            cleanWs()
        }
    }
}
