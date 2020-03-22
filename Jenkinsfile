pipeline {
  
  agent any
  tools {nodejs "node"}
    stages {
	    stage('React APP deployment') {
	        steps {
                sh "npm install"
                sh "npm install forever --save"
                sh "npm install lighthouse --save"
                sh "forever start -c 'npm start' ./"
            }
        }

        stage('Performance Tests') {
            steps {
                sh "npm run lighthouse"
                sh "forever stop 0" 
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
