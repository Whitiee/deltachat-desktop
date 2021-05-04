pipeline {
    agent any

    stages {
    
        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }
    
        stage('Test') {
            steps {
                echo 'Testing..'
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
            attachLog: true,
            mail to: 'juliafajer69@gmail.com',
            subject: "Failed test Pipeline: ${currentBuild.fullDisplayName}",
            body: "Something is wrong with ${env.BUILD_URL}"
        }
    }
    
}
