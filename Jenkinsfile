pipeline {
    agent any

    stages {
        stage('Clean Workspace') {
            steps {
                sh 'rm -rf node_modules'
                sh 'npm cache clean --force'
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
