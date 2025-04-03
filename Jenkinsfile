pipeline {
    agent any

    tools {
        maven 'Maven 3.8.1'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                git branch: 'main',
                    credentialsId: '6102de68-ebf3-4296-8dae-0ac426361d35',
                    url: 'https://github.com/aikansh-bits/Devops_Assignment'
            }
        }

        stage('Build') {
            steps {
                echo 'Building with Maven...'
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                sh 'mvn test'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Simulating deployment to staging...'
                sh 'echo Deploying to staging server...'
            }
        }

        stage('Approval') {
            steps {
                input message: 'Do you want to deploy to production?', ok: 'Deploy'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
                sh 'echo Deploying to production server...'
            }
        }
    }

    post {
        success {
            echo 'Pipeline finished successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}
