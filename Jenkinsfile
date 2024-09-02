pipeline {
    agent any

    stages {
        // stage('Clean Workspace') {
        //     steps {
        //         deleteDir()
        //     }
        // }
        stage('Build') {
            // agent {
            //     docker {
            //         image 'node:18-alpine'
            //         reuseNode true
            //     }
            // }
            environment {
                NPM_CONFIG_CACHE = './.npm-cache' // Set a local npm cache directory
            }
            steps {
                sh '''
                   
                    node --version
                    npm --version
                    npm install
                    #npm ci
                    npm run build
                '''
            }
        }
    }
}
