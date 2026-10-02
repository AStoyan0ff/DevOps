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

        stage('Check Node.js') {
            steps {
                bat 'node --version'
                bat 'call npm.cmd --version'
            }
        }

        stage('Install dependencies') {
            steps {
                bat 'call npm.cmd ci'
            }
        }

        stage('Run tests') {
            steps {
                bat 'call npm.cmd test'
            }
        }
    }
}