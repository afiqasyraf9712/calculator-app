pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-node-app:1.0 .' // Build Docker image
            }
        }
        
        stage('Push Docker Image') {
            steps {
                withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhubpwd')]) {
                    sh 'docker login -u munajatadnan -p ${dockerhubpwd}' // Docker login
                    sh 'docker tag my-node-app:1.0 capstone_project/v1.0' // Docker tag
                    sh 'docker push munajatadnan/my-node-app:1.0' // Docker push
                }
            }
        }
    }
}
