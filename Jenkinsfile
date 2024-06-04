pipeline {
    agent any
    stages {
        stage('Install Node.js') {
            // Install Node.js using the NodeJS plugin
            steps {
                script {
                    def nodejsInstallation = tool name: 'nodejs-21.0.0', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
                    env.PATH = "${nodejsInstallation}/bin:${env.PATH}"
                }
            }
        }
        
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Test') {
            steps {
                sh 'npm install' // Install npm dependencies
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
