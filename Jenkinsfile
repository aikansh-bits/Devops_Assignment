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
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                bat 'mvn test'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Simulating deployment to staging...'
                bat 'echo Copying build to staging environment...'
                bat 'if not exist staging mkdir staging'
                bat 'copy target\\*.jar staging\\'
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
                bat 'if not exist production mkdir production'
                bat 'copy target\\*.jar production\\'
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            echo 'Pipeline finished successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}