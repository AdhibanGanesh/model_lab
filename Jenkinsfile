pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/AdhibanGanesh/model_lab.git', branch: 'master'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker stop $(docker ps -q --filter "ancestor=app") || true'
                    sh 'docker build -t app .'
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker run -d -p 8081:80 app'
                }
            }
        }
    }
}