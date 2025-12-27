pipeline {
    agent any

    stages {
        stage('get_code') {
            steps {
                sh '''
                   cd ~/jenkins-demo
                   git pull origin main
                '''   
            }
        }
        stage('Build_deploy') {
            steps {
                sh '''
                   cd ~/jenkins-demo
                   docker build -t jenkins1 .
                   docker stop dev1
                   docker rm dev1
                   docker run --name dev1 -p 8500:80 -d jenkins1
                '''
            }
        }
    }
}
