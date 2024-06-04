pipeline {
    agent any

    environment {
        NODEJS_HOME = tool name: 'nodejs-20.14.0', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
        PATH = "${NODEJS_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Check npm') {
            steps {
                script {
                    // Print PATH for debugging
                    sh 'echo $PATH'

                    // Ensure npm is installed and available
                    sh 'npm --version'
                }
            }
        }
    }
}
