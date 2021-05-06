pipeline {

	agent any

    stages {
	     stage('Build') {
            steps {
                echo 'Build..'
		sh 'apt install npm -y'
                sh 'npm i npm@latest -g'
                sh 'npm fund'
		sh 'npm config set prefix "~/.npm-global"'
		sh 'export PATH=~/.npm-global/bin:$PATH'
		sh './.profile'
                sh 'npm install -g jshint'
            }
	  }
        stage('Test') {
            steps {
                echo 'Testing..'
		sh 'npm run test'
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
