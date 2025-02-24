pipeline {
    agent any

    stages {
        stage ('Git Checkout') {
            steps {
                // Using the personal access token for GitHub authentication
                git branch: 'main', 
                    credentialsId: 'Vamshi5S', // Use the credentialsId associated with your PAT in Jenkins
                    url: 'https://github.com/Vamshi5S/learn-jenkins-app.git'
            }
        }
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
