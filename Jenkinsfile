pipeline {
    agent any

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
