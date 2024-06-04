pipeline {
    agent any

    stages {
        stage('Check npm') {
            steps {
                script {
                    // Ensure npm is installed and available
                    sh 'npm --version'
                }
            }
        }
    }
}
