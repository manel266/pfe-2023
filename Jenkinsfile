pipeline {
    agent any

    stages {
        stage('Build du projet') {
            agent {
                docker {
                    image 'maven:3-alpine'
                    args '-v $HOME/.m2:/root/.m2' // Mounting Maven local repository
                }
            }
            steps {
                echo 'Building..'
                sh 'mvn clean install'
            }
        }

        stage('Login') {
            steps {
                sh 'docker login --username=4587612 --password=Sesame2022'
            }
        }

        stage('Construction image') {
            steps {
                script {
                    unstash 'targetfiles'
                    sh 'docker build . -t azure-back:test'
                    sh 'docker tag azure-back:test 4587612/azure-back:test'
                    sh 'docker push 4587612/azure-back:test'
                }
            }
        }
    }
}
