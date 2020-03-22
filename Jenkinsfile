pipeline {
  
  agent {
        docker {
            image 'node:13-alpine' 
            args '-p 3000:3000' 
        }
    }
  
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh '''set -x && set +x && set -x && npm test'''
            }
        }
        stage('Deliver') {
            steps {
                sh ''' set -x && npm run build && set +x && set -x && npm start & sleep 1 && echo $! > .pidfile && set +x '''
                sh ''' npm run lighthouse'''
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh '''set -x && kill $(cat .pidfile)'''
            }
        }
    }
}
