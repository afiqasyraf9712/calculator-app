pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Test') {
            steps {
                sh 'sudo apt install npm'
                sh 'npm test'
            }
        }
        
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        
        stage('Build Image') {
            steps {
                sh 'docker build -t my-node-app:1.0 .'
            }
        }
        
        stage('Docker Push') {
            steps {
                withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhubpwd')]) {
                    sh 'docker login -u munajatadnan -p ${dockerhubpwd}'
                    sh 'docker tag my-node-app:1.0 capstone_project/v1.0'
                    sh 'docker push munajatadnan/devops-integration'
                }
            }
        }
    }
}
