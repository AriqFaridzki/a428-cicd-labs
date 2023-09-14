    pipeline {
        agent {
            docker {
                image 'node:16-buster-slim'
                args '-p 3000:3000'
            }
        }
        stages {
            stage('Build') {
                steps {
                    sh 'npm install'
                }
            }
            stage('Test') {
                steps {
                    sh './jenkins/scripts/test.sh'
                }
            }
            stage('Manual Approval') {
                steps {
                    sh './jenkins/scripts/deliver.sh'
                    input message: 'Lanjutkan ke tahap Deploy? (Klik "Proceed" untuk Melanjutkan)'
                }
            }
            stage('Deploy'){
                steps{
                    sleep 1s
                    sh 'Holding instance for 1 minute.....'
                    sleep 1m
                    sh 'Terminating Instance....'
                    sleep 1s
                    sh './jenkins/scripts/kill.sh' 
                }
            }
        }
    }