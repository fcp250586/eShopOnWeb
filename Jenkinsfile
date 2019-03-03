pipeline {
  agent any
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
      echo 'Done.'
    }
  }
}