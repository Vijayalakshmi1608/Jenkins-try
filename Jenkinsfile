pipeline {
    agent any
    environment {
        IMAGE = "myapp:${BUILD_NUMBER}"
    }
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t myapp .'
                }
            }
        }
        stage('Push to DockerHub') {
            steps {
                withCredentials([string(credentialsId: 'dockerhub-token', variable: 'TOKEN')]) {
                    sh 'echo $TOKEN | docker login -u myusername --password-stdin'
                    sh 'docker push myapp'
                }
            }
        }
    }
}
