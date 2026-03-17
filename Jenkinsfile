pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install dependencies') {
            agent {
                docker {
                    image 'node:18-alpine'
                    args '-u root:root'
                }
            }
            steps {
                sh 'npm install'
            }
        }

        stage('Run tests') {
            agent {
                docker {
                    image 'node:18-alpine'
                    args '-u root:root'
                }
            }
            steps {
                sh 'npm test'
            }
        }

        stage('Build Docker image') {
            steps {
                sh 'docker build -t devsecops-jenkins-eliorproject:jenkins .'
            }
        }
    }
}
