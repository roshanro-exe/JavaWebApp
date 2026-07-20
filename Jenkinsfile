pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                checkout scm
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t javawebapp:v1 .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker rm -f javawebapp || true'
                sh 'docker run -d --name javawebapp -p 8081:8080 javawebapp:v1'
            }
        }
    }
}
