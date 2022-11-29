pipeline {
    agent {
        docker {
            image 'node:19-alpine3.15' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'nvm install' 
            }
        }

         stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }

         stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}