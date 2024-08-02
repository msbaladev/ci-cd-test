pipeline {
    agent any

    tools {
        nodejs 'node server' // Use the name you configured in Global Tool Configuration
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/msbaladev/ci-cd-test.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build' // Adjust this command based on your build process
            }
        }

        stage('Test') {
            steps {
                sh 'npm test' // Adjust this command based on your testing process
            }
        }

        stage('Deploy') {
            steps {
                // Deployment steps (e.g., uploading to a server or a cloud service)
                // Example: sh 'scp -r ./dist user@server:/path/to/deploy'
            }
        }
    }

    post {
        always {
            // Clean up workspace or other post-build actions
            cleanWs()
        }
    }
}
