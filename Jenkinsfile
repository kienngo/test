pipeline {
    agent any

    environment {
        dotnet = 'C:\\Program Files\\dotnet\\dotnet.exe'
    }

    stages {
        stage('Build') {
            steps {
				bat 'dotnet restore Wiseman.PJC.Service.GroupSettings.sln'
                bat 'dotnet build Wiseman.PJC.Service.GroupSettings.sln --configuration Release'
            }
        }

        stage('Test') {
            steps {
                bat 'dotnet test Wiseman.PJC.Service.GroupSettings.WebApi\\Wiseman.PJC.Service.GroupSettings.WebApi.csproj'
            }
        }

        stage('Release') {
            steps {
                bat 'dotnet build Wiseman.PJC.Service.GroupSettings.sln /p:PublishProfile=" Properties\\PublishProfiles\\FolderProfile.pubxml" /p:Platform="Any CPU" /p:DeployOnBuild=true /m'
            }
        }
    }
}
