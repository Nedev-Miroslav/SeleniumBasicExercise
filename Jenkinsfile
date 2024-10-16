pipeline {
    agent any
    triggers{
        pollSCM('* * * * *')
    }
    stages {
        stage('Checkout the repo') {
            steps {
                checkout scm
            }
        }
        stage('Restore dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }
        stage('Build') {
            steps {
                bat 'dotnet build --no-restore'
            }
        }
        stage('Run UI tests') {
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}
