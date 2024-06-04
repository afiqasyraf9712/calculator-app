pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Test') {
            steps {
                sh 'wsl npm install' // Install npm dependencies within WSL
                sh 'wsl npm test'    // Run tests within WSL
            }
        }
        
        stage('Build') {
            steps {
                sh 'wsl npm run build' // Build within WSL
            }
        }
        
        stage('Build Docker Image') {
            steps {
                sh 'wsl docker build -t my-node-app:1.0 .' // Docker build within WSL
            }
        }
        
        stage('Push Docker Image') {
            steps {
                withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhubpwd')]) {
                    sh 'wsl docker login -u munajatadnan -p ${dockerhubpwd}' // Docker login within WSL
                    sh 'wsl docker tag my-node-app:1.0 capstone_project/v1.0' // Docker tag within WSL
                    sh 'wsl docker push munajatadnan/my-node-app:1.0' // Docker push within WSL
                }
            }
        }
    }
}
