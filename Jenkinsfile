pipeline {
    agent any

    stages {
    
        stage('Install dependencies') {
            steps {
           	echo 'Starting pipeline..'
		nodejs(nodeJSInstallationName: 'Node 6.x', configId: '<config-file-provider-id>') {
                sh 'npm config ls'
                }
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
