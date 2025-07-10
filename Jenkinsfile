pipeline {
    agent any

    environment {
        IMAGE = "192.168.64.26:5000/myapp"
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/kullanici/myapp.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE .'
            }
        }

        stage('Push to Registry') {
            steps {
                sh 'docker push $IMAGE'
            }
        }

        stage('Deploy to K8s') {
            steps {
                sh 'kubectl apply -f k8s/deployment.yaml'
            }
        }
    }
}

