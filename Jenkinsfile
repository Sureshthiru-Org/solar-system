pipeline {
    agent any
    tools {
        nodejs 'nodejs-23.9.0'
    }

    stages {
        stage('VM node check') {
            steps {
                sh '''
                    npm -v 
                    node -v
                '''
            }
        }
    }
} 
