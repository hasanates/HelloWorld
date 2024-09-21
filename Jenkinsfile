pipeline {
    agent any
    stages {
        stage('Restore') {
            steps {
                script {
                    // Restore .NET dependencies for the solution
                    sh 'dotnet restore HelloWorld.sln'
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    // Build the solution in Release configuration
                    sh 'dotnet build HelloWorld.sln --configuration Release'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Run tests for the solution
                    sh 'dotnet test HelloWorld.sln --no-build'
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
