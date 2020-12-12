pipeline {
    agent any
    
    tools {nodejs "node"}
    
    stages {
        stage('Cloning repository') {
            steps {
                git 'https://github.com/AlicjaBielska/node-mssql'
            }
        }
        stage('Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Linter') {
            steps {
                sh 'npm run lint'
            }
        }
        stage('Tests') {
            parallel {
                stage('unit') {
                    steps {
                        sh 'npm run test-unit'
                    }
                }
                stage('tedious') {
                    steps {
                        sh 'npm run test-tedious'
                    }
                }
                stage('cli') {
                    steps {
                        sh 'npm run test-cli'
                    }
                }
            }
        }
    }
}