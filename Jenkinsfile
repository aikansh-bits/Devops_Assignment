pipeline {
    agent any

    tools {
        maven 'Maven 3.8.1' // Set this to the name configured in Jenkins global tools
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                git credentialsId: '6102de68-ebf3-4296-8dae-0ac426361d35', url: 'https://github.com/aikansh-bits/Devops_Assignment'
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
                // Replace this with real deployment commands like SSH, SCP, etc.
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
                // Replace this with actual production deployment steps
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
