pipeline {
    agent any

    stages {

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