pipeline {
    agent {
        docker {
            image 'node:12-alpine'
            args '-p 3000:3000 -p 5000:5000' 
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'touch /root/.bash_profile'
                sh 'npm install mirror-config-china --registry=https://registry.npm.taobao.org'
                sh 'npm run mirror-config-china --registry=https://registry.npm.taobao.org'
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
    }
}