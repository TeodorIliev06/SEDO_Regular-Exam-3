pipeline {
    agent any
    
    triggers {
        pollSCM('H/5 * * * *')
    }
    
    stages {
        stage("Build .NET Project") {
            steps {
                sh 'dotnet build'
            }
        }
        
        stage("Run Unit and Integration Tests") {
            steps {
                sh 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}