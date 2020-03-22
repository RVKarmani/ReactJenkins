pipeline {

  agent any
  stages {

  stage('Performance Tests') {
  steps {
    deleteDir()
    checkout scm
    bat label:'NPM', script:'npm install'
    bat label:'Forever',script:'forever start -c "npm start" ./'
    bat label:'Light',script:'npm run lighthouse'
    
  }
    post {
    always {
      publishHTML (target: [
        allowMissing: false,
        alwaysLinkToLastBuild: false,
        keepAll: true,
        reportDir: '.',
        reportFiles: 'lighthouse-report.html',
        reportName: "Lighthouse"
      ])
    }
  }
}



}
}
