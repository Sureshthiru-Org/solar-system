pipeline {
    agent any
    tools {
        nodejs 'nodejs-23.9.0'
    }

    stages {
        stage('Installing Dependency') {
            steps {
                sh 'npm install --no-audit'
            }
        }

        stage('NPM Dependency Audit') {
            steps {
                sh '''
                    npm audit --audit-level=critical
                    echo $?
                '''
            }
        }
    }
}
