pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Check .NET SDK') {
            steps {
                bat 'dotnet --version'
            }
        }

        stage('Restore') {
            steps {
                bat 'dotnet restore HouseRentingSystem.sln'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build HouseRentingSystem.sln --no-restore'
            }
        }

        stage('Test') {
            steps {
                bat 'dotnet test HouseRentingSystem.sln --no-build --logger trx'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/TestResults/*.trx',
                             allowEmptyArchive: true
        }
    }
}