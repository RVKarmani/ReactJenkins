pipeline {
  
  agent {
        docker {
            image 'node:13-alpine' 
            args '-p 3000:3000' 
        }
    }
  
    stages {
	    
	    stage('NODE Build') {
	        steps {
                sh "npm install"
                sh "npm install forever -g"
                sh "npm install lighthouse --save"
            }
       	}
	    
	    stage('React APP deployment') {
	        steps {
                sh "forever start -c 'npm start' ./"
            }
        }
    }
}
