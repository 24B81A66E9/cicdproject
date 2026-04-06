pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t myapp:latest .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker rm -f myapp_container || true'
                sh 'docker run -d -p 8080:8080 --name myapp_container myapp:latest'
            }
        }
    }
}
