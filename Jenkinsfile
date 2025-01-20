pipeline {
    agent any

    environment {
        DOTNET_CLI_HOME = "${env.WORKSPACE}/.dotnet"
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the repository
                git 'https://github.com/salman1256/MyDotNetApp.git'
            }
        }

        stage('Restore') {
            steps {
                // Restore the NuGet packages
                script {
                    sh 'dotnet restore'
                }
            }
        }

        stage('Build') {
            steps {
                // Build the application
                script {
                    sh 'dotnet build --configuration Release'
                }
            }
        }

        stage('Test') {
            steps {
                // Run the tests
                script {
                    sh 'dotnet test --no-build --verbosity normal'
                }
            }
        }

        stage('Publish') {
            steps {
                // Publish the application
                script {
                    sh 'dotnet publish --configuration Release --output ./publish'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}