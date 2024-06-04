pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                sh 'npm install' // Install npm dependencies using WSL
            }
        }
        
        stage('Build Docker Image') {
            steps {
                echo "Path is ${env.$PATH}"
                sh 'docker build -t my-node-app:1.0 .'
            }
        }

        stage('Build Image') {
            steps {
                script {
                    docker.build("capstone/calculatorapp", "-f /home/afiqasyraf9712/calculator-app/calculator-application-monitoring-app/Dockerfile /home/afiqasyraf9712/calculator-app/calculator-application-monitoring-app")
                }
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
