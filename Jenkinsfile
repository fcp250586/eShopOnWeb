pipeline {
  agent { node 'eshop' }
  stages {
    stage('Checkout') {
      steps {
        checkout scm
        sh 'git clean -xfd'
      }
    }
    stage('Build') {
      steps {
        sh 'dotnet restore'
        sh 'dotnet build'
      }
    }
    stage('Test') {
      steps {
        sh 'dotnet test'
      }
    }
  }
  post {
    always {
      step ([$class: 'MSTestPublisher', testResultsFile:"**/TestResults/UnitTests.trx", failOnError: true, keepLongStdio: true])
      echo 'Done.'
    }
  }
}