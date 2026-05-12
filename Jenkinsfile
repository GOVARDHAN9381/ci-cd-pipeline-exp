pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/GOVARDHAN9381/ci-cd-pipeline-exp.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-cicd-app .'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'docker run --rm flask-cicd-app python -m py_compile app.py'
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'docker stop flask-container || true'
                sh 'docker rm flask-container || true'
                sh 'docker run -d -p 5000:5000 --name flask-container flask-cicd-app'
            }
        }
    }
}