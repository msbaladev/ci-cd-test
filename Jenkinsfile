pipeline {
    agent any

    tools {
        nodejs 'node server' // Ensure 'node server' is the name of the Node.js installation configured in Jenkins
    }

    stages {
        stage('Prepare Workspace') {
            steps {
                script {
                   git url: 'https://github.com/msbaladev/ci-cd-test.git', credentialsId: 'github-pat', branch: 'main'
                }
            }
        }
        stage('Install Dependencies') {
            steps {
                sh "npm install"
            }
        }
        stage('Build') {
            steps {
                echo 'npm run build...'
                sh 'npm run build' // If you have a build script in your package.json
            }
        }
        stage('Deploy') {
            steps {
                sh 'pm2 restart ecosystem.config.cjs'
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}




//    steps {
//                 script {
//                     // Check if the workspace directory exists
//                     if (fileExists('.git')) {
//                         // If it exists, pull the latest changes
//                         sh 'git reset --hard HEAD'
//                         sh 'git pull origin main'
//                     } else {
//                         // If it does not exist, clone the repository
//                         git url: 'https://github.com/msbaladev/ci-cd-test.git', credentialsId: 'github-pat', branch: 'main'
//                     }
//                 }
//             }