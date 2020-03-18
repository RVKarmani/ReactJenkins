pipeline {

  agent any
  stages {

  stage('Performance Tests') {
  steps {
    deleteDir()
    checkout scm
    bat label: 'NPM version' running', script: '''npm --version'''
  }
}



}
}