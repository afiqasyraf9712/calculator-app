pipeline {
    agent any

    environment {
        NODEJS_HOME = tool name: 'nodejs-22.2.0', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
        PATH = "${NODEJS_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Setup Node.js and npm') {
            steps {
                script {
                    // Ensure npm is installed and available
                    sh 'npm --version'
                }
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build docker image') {
            steps {
                script {
                    sh 'docker build -t munajatadnan/devops-integration .'
                }
            }
        }

        stage('Push image to Hub') {
            steps {
                script {
                    withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhubpwd')]) {
                        sh 'docker login -u munajatadnan -p ${dockerhubpwd}'
                    }
                    sh 'docker push munajatadnan/devops-integration'
                }
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            junit 'test-results/**/*.xml'
        }
    }
}
