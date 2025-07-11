pipeline {
    agent any

    environment {
        IMAGE = "192.168.64.26:5000/myapp:v3"
    }

    stages {
        stage('Clone') {
            steps {
                git url: 'https://github.com/Groom78/HelloWorld.git',
                    branch: 'main'
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
                sh 'kubectl apply -k .'
            }
        }
    }
}
