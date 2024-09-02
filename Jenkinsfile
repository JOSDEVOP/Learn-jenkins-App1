pipeline {
    agent any
    stages {
        stage('Clean Workspace') {
    steps {
        deleteDir()
    }
}

        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                    // args' -u node'
                }
            }
            steps {
                // cleanWs()
                sh '''
                #chown -R $(id -u):$(id -g) .
                #chmod -R 755 .

                pwd
                ls -la
                npm --version
                node --version
                npm ci --verbose --unsafe-perm

                npm run build
                
                ls -la
                '''
            }
        }
        stage('Test') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                test -f build/index.html
                npm test
                '''
                archiveArtifacts artifacts: 'test-results/**'
            }
        }
        stage('E2E') {
            agent {
                docker {
                    image 'mcr.microsoft.com/playwright:v1.46.1-jammy'
                    reuseNode true
                }
            }
            steps {
                sh '''
                npm install serve
                node_modules/.bin/serve -s build
                npx playwright test
                '''
            }
        }
    }
    // post {
    //     success {
    //         archiveArtifacts artifacts: 'build/**'
    //     }
    // }
}