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

        stage(' Dependency Scanning') {
            parallel {   
                stage('NPM Dependency Audit') {
                    steps {
                        sh '''
                            npm audit --audit-level=critical
                            echo $?
                        '''
                    }
                }

                stage('OWASP dependency check') {
                    steps {
                        dependencyCheck additionalArguments: '''
                            --scan \'./\'
                            --out \'./\'
                            --format \'ALL\'
                            --prettyPrint 
                            --noupdate''', odcInstallation: 'OWASP-dependency_check-10'
                        
                        dependencyCheckPublisher failedTotalCritical: 3, pattern: 'dependency-check-report.xml', skipNoReportFiles: true, stopBuild: true
                    }
                }
            }
        }
        stage('Unit testing') {
            steps {
                sh 'npm test' 
            }
        }
    }
}

