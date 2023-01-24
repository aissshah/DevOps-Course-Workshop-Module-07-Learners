pipeline {
  agent none

  stages {
    stage('Build and Test C#') {
      agent {
        docker {
          image 'mcr.microsoft.com/dotnet/sdk:6.0'
        }
      }
      environment {
        DOTNET_CLI_HOME = '/tmp/DOTNET_CLI_HOME'
        XDG_DATA_HOME = '/tmp'
      }

      steps {
        echo 'Building...'
        sh 'dotnet build'
        echo 'Running tests...'
        sh 'dotnet test'
      }
    }
    stage('Build and Test TS') {
      agent {
        docker { 
          image 'node:16.13.1-alpine' 
        }
      }
      steps {
        dir('./DotnetTemplate.Web') {
          sh 'node --version'
          sh 'npm install'
          sh 'npm run build'
          echo 'Running tests...'
          sh 'npm t'
          sh 'npm run lint'
        }
      }
    }
  }
}