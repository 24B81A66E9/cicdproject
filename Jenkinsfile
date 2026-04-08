pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/24B81A66E9/cicdproject.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t student-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f student-container || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 8081:8080 --name student-container student-app'
            }
        }
    }
}
