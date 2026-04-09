pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: "${env.BRANCH_NAME}", url: 'https://github.com/2kita9/cicd-jenkins-pipeline-task.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh 'echo Running Tests...'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'main') {
                        sh 'docker build -t myapp:main .'
                    } else {
                        sh 'docker build -t myapp:dev .'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'main') {
                        sh 'echo Deploying MAIN on port 3000'
                    } else {
                        sh 'echo Deploying DEV on port 3001'
                    }
                }
            }
        }

    }
}
