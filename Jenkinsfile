pipeline {
    agent any

    stages {
        
    //     stage('Clean Workspace') {
    // agent {
    //             docker {
    //                 image 'node:18-alpine'
    //                 reuseNode true
    //             }
    //         }

    //         steps {
    //             deleteDir()
    //         }
    //     }
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            // environment {
            //     NPM_CONFIG_CACHE = './.npm-cache' // Set a local npm cache directory
            // }
            steps {
                sh '''
                    #npm cache clean --force
                    node --version
                    npm --version
                    npm ci
                    npm run build
                '''
            }
        }
    }
}
