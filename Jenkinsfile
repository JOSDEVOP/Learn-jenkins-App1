pipeline {
    agent any

    stages {
        stage('Clean Workspace') {
            steps {
                deleteDir() // This will remove the entire workspace, ensuring a clean slate
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
                    npm cache clean --force
                    node --version
                    npm --version
                    npm ci
                    npm run build
                '''
            }
        }
    }
}
