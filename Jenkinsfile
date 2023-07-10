pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Backend') {
            agent {
                docker {
                    image 'node:14-alpine'
                    args '-v $HOME/.npmrc:/root/.npmrc'
                }
            }
            steps {
                dir('backend') {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }

        stage('Build Frontend') {
            agent {
                docker {
                    image 'node:14-alpine'
                    args '-v $HOME/.npmrc:/root/.npmrc'
                }
            }
            steps {
                dir('frontend') {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }

        stage('Test') {
            agent {
                docker {
                    image 'node:14-alpine'
                    args '-v $HOME/.npmrc:/root/.npmrc'
                }
            }
            steps {
                dir('backend') {
                    sh 'npm run test'
                }
                dir('frontend') {
                    sh 'npm run test'
                }
            }
        }

        stage('Deploy') {
            steps {
                dir('backend') {
                    sh 'npm run deploy'
                }
            }
        }
    }
}
