pipeline {
    agent {
        docker {
            image 'node:16-buster-slim'
            args '-p 3000:3000 --memory=2g'
        }
    }
    stages {
        stage('Build') {
            steps {
                timeout(time: 30, unit: 'MINUTES') {
                    sh 'npm cache clean --force'
                    sh 'npm install --unsafe-perm=true'
                }
            }
        }

        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
    }
}
