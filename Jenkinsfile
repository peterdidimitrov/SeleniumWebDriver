pipeline {
    agent { label 'ubuntu-latest' }
    
    environment {
        CHROMEWEBDRIVER = '/usr/bin/google-chrome'
    }

    stages {
        stage('Checkout code') {
            steps {
                // Check out the code from the repository
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], 
                    userRemoteConfigs: [[url: 'https://github.com/your-repo-url.git']]
                ])
            }
        }

        stage('Setup .NET Core') {
            steps {
                sh 'wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb'
                sh 'sudo dpkg -i packages-microsoft-prod.deb'
                sh 'sudo apt-get update; sudo apt-get install -y apt-transport-https && sudo apt-get update && sudo apt-get install -y dotnet-sdk-6.0'
            }
        }

        stage('Install Chrome') {
            steps {
                sh 'sudo apt-get update'
                sh 'sudo apt-get install -y google-chrome-stable'
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'dotnet restore SeleniumBasicExercise.sln'
            }
        }

        stage('Build') {
            steps {
                sh 'dotnet build SeleniumBasicExercise.sln --no-restore'
            }
        }

        stage('Run TestProject1 tests') {
            steps {
                echo 'Running TestProject1 tests'
                sh 'dotnet test TestProject1/TestProject1.csproj --verbosity normal'
            }
        }

        stage('Run TestProject2 tests') {
            steps {
                echo 'Running TestProject2 tests'
                sh 'dotnet test TestProject2/TestProject2.csproj --verbosity normal'
            }
        }

        stage('Run TestProject3 tests') {
            steps {
                echo 'Running TestProject3 tests'
                sh 'dotnet test TestProject3/TestProject3.csproj --verbosity normal'
            }
        }
    }
}
