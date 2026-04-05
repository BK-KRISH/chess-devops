pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git 'https://github.com/BK-KRISH/chess-devops.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                dir('app') {
                    sh 'docker build -t bk-chess-app .'
                }
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop chess-container || true'
                sh 'docker rm chess-container || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 80:80 --name chess-container bk-chess-app'
            }
        }
    }
}