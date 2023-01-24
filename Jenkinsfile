pipeline {
  agent none

  stages {
    // stage ('Clean workspace') {
    //   steps {
    //     cleanWs()
    //   }
    // }
    stage('Build C#') {
      agent {
        docker {
          image 'mcr.microsoft.com/dotnet/sdk:7.0'
        }
      }
      environment {
        DOTNET_CLI_HOME = '/tmp/DOTNET_CLI_HOME'
        XDG_DATA_HOME = '/tmp'
      }

      steps {
        echo 'Building...'
        sh 'dotnet build'
      }
    }
    stage('Build node') {
      agent {
        docker { 
          image 'node:16.13.1-alpine' 
        }
      }
      steps {
        dir './DotnetTemplate.Web'
        sh 'node --version'
      }
    }
  }
}