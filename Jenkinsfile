pipeline {
    agent any
    stages {
        stage('Install Node.js') {
            steps {
                script {
                    def nodejsInstallation = tool name: 'nodejs-22.2.0', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
                    env.PATH = "${nodejsInstallation}/bin:${env.PATH}"
                }
            }
        }
        
        stage('Test') {
            steps {
                sh 'npm init -y'
                sh 'npm install express'
                sh 'npm install prom-client'
                sh 'npm install' // Install npm dependencies using WSL
            }
        }
        
        stage('Build') {
            steps {
                sh 'npm start'
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
