pipeline {
  agent any

  stages {
    stage ('Clean workspace') {
      steps {
        cleanWs()
      }
    }
    stage('Build') {
      steps {
        echo 'Building...'
        sh 'run dotnet build'
      }
    }
  }
}