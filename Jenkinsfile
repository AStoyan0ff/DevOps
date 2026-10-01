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

        stage('Restore') {
            steps {
                bat 'dotnet restore SeleniumBasicExercise.sln'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build SeleniumBasicExercise.sln --no-restore'
            }
        }

        stage('Test Project 1') {
            steps {
                bat 'dotnet test TestProject1/TestProject1.csproj --no-build --logger trx'
            }
        }

        stage('Test Project 2') {
            steps {
                bat 'dotnet test TestProject2/TestProject2.csproj --no-build --logger trx'
            }
        }

        stage('Test Project 3') {
            steps {
                bat 'dotnet test TestProject3/TestProject3.csproj --no-build --logger trx'
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