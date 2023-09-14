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
                    sh 'Holding instance for 1 minute.....'
                    sleep(time: 1, unit: 'MINUTES')
                    sh 'Terminating Instance....'
                    sleep(time: 1, unit: 'SECONDS')
                    sh './jenkins/scripts/kill.sh' 
                }
            }
        }
    }