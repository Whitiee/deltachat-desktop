pipeline {
    agent {
	docker {
          image 'node:10.11.0-alpine'
        }
    }
	
    stages {
        stage('Test') {
            steps {
                echo 'Testing..'
		sh "npm install"
         	sh 'npm test'
            }
        } 
    }
    
    post {
        always {
            echo 'I have finished'
        }
        success {
            echo 'I succeeded!'
        }
        failure {
            echo 'I failed :('
            emailext attachLog: true, 
            	     body: "Something is wrong with ${env.BUILD_URL}",
            	     subject: "Failed test Pipeline: ${currentBuild.fullDisplayName}",
            	     to: 'juliafajer69@gmail.com'
        }
    }
}
