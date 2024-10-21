pipeline {
    agent any

    stages {
        stage('Setup .NET Core') {
            steps {
                bat 'wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb'
                bat 'sudo dpkg -i packages-microsoft-prod.deb'
                bat 'sudo apt-get update; sudo apt-get install -y apt-transport-https && sudo apt-get update && sudo apt-get install -y dotnet-sdk-6.0'
            }
        }

        stage('Install Chrome') {
            steps {
                bat 'sudo apt-get update'
                bat 'sudo apt-get install -y google-chrome-stable'
            }
        }

        stage('Install dependencies') {
            steps {
                bat 'dotnet restore SeleniumBasicExercise.sln'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build SeleniumBasicExercise.sln --no-restore'
            }
        }

        stage('Run TestProject1 tests') {
            steps {
                echo 'Running TestProject1 tests'
                bat 'dotnet test TestProject1/TestProject1.csproj --verbosity normal'
            }
        }

        stage('Run TestProject2 tests') {
            steps {
                echo 'Running TestProject2 tests'
                bat 'dotnet test TestProject2/TestProject2.csproj --verbosity normal'
            }
        }

        stage('Run TestProject3 tests') {
            steps {
                echo 'Running TestProject3 tests'
                bat 'dotnet test TestProject3/TestProject3.csproj --verbosity normal'
            }
        }
    }
}