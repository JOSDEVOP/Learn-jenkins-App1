pipeline {
    agent any

    stages {
        // stage('Clean Workspace') {
        //     steps {
        //         deleteDir()
        //     }
        // }
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            
            steps {
                sh '''
                   
                    node --version
                    npm --version
                    npm ci
                  
                    npm run build
                '''
            }
        }
    }
}
