pipeline {
    agent any

    stages {
        stage('Init') {
            steps {
                sh 'docker stop -f $(docker ps -q) || true'
                sh 'docker rm -f $(docker ps -qa) || true'
            }
        }
        stage('build') {
            steps {
                sh 'docker build -t node-img .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -d -p 80:5000 --name node-app node-img:latest'
            }
        }
    }
}