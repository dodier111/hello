pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from version control
                git 'https://github.com/dodier111/hello.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install Node.js and npm
                sh 'sudo apt update'
                sh 'sudo apt install -y nodejs npm'
                sh 'npm install'
            }
        }

        stage('Deploy') {
            steps {
                // Start the Node.js application using PM2
                sh 'npm install -g pm2'
                sh 'pm2 start index.js'
            }
        }
    }

    post {
        always {
            // Clean up or perform any other post-build actions
            sh 'pm2 logs' // Display logs for debugging (optional)
        }
    }
}
