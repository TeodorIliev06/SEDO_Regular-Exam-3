pipeline {
    agent {
        docker {
            image 'mcr.microsoft.com/dotnet/sdk:8.0'
        }
    }
    
    triggers {
        pollSCM('H/5 * * * *')
    }
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code...'
                checkout scm
            }
        }
        
        stage('Restore Dependencies') {
            steps {
                echo 'Restoring .NET dependencies...'
                sh 'dotnet restore Horizons.sln'
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'dotnet build Horizons.sln --configuration Release --no-restore'
            }
        }
        
        stage('Run Unit Tests') {
            steps {
                echo 'Running unit tests...'
                sh 'dotnet test Horizons.Tests.Unit/Horizons.Tests.Unit.csproj --configuration Release --no-build --verbosity normal'
            }
        }
        
        stage('Run Integration Tests') {
            steps {
                echo 'Running integration tests...'
                sh 'dotnet test Horizons.Tests.Integration/Horizons.Tests.Integration.csproj --configuration Release --no-build --verbosity normal'
            }
        }
    }
}