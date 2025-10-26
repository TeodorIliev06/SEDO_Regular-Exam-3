pipeline {
    agent any

    // Use 'bat' for windows installation, 'sh' for linux (personally I use 'sh' for docker)
    // Add environment block if .NET is not in system path (if needed)
    
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
